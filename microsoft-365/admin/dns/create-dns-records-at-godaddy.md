---
title: Połączenie rekordy DNS w witrynie GoDaddy do Microsoft 365
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
description: Dowiedz się, jak zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, Skype dla firm Online i innych usług w witrynie GoDaddy dla firmy Microsoft.
ms.openlocfilehash: 6cf110b55c76ce6c857f13dcd5b0075b309b654f
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780352"
---
# <a name="connect-your-dns-records-at-godaddy-to-microsoft-365"></a>Połączenie rekordy DNS w witrynie GoDaddy do Microsoft 365

 **[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji.

Jeśli witryna GoDaddy jest Twoim dostawcą hostingu DNS, wykonaj czynności opisane w tym artykule, aby zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, usługi Skype dla firm Online i tym podobne.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Istnieją dwie opcje konfigurowania rekordów DNS dla domeny:

- [**Użyj Połączenie domeny**](#use-domain-connect-to-verify-and-set-up-your-domain) Jeśli nie skonfigurowano domeny z innym dostawcą usług poczty e-mail, wykonaj kroki Połączenie domeny, aby automatycznie zweryfikować i skonfigurować nową domenę do użycia z Microsoft 365.

   LUB

- [**Wykonaj kroki ręczne**](#create-dns-records-with-manual-setup) Zweryfikuj domenę, wykonując poniższe kroki ręcznie, i wybierz, kiedy i które rekordy należy dodać do rejestratora domeny. Dzięki temu można skonfigurować nowe rekordy MX (poczty e-mail), na przykład dla Twojej wygody.

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>Weryfikowanie i konfigurowanie domeny przy użyciu Połączenie domeny

Wykonaj następujące kroki, aby automatycznie zweryfikować i skonfigurować domenę GoDaddy przy użyciu Microsoft 365:

1. W Centrum administracyjne platformy Microsoft 365 wybierz pozycję **Ustawienia** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domeny**</a> i wybierz domenę, którą chcesz skonfigurować.

1. Wybierz trzy kropki (więcej akcji), > wybierz pozycję **Rozpocznij instalację**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Wybierz pozycję Rozpocznij konfigurację.":::

1. Na stronie Jak chcesz połączyć domenę? wybierz pozycję **Kontynuuj**.

1. Na stronie Dodawanie rekordów DNS wybierz pozycję **Dodaj rekordy DNS**.

1. Na stronie logowania GoDaddy zaloguj się do swojego konta i wybierz pozycję **Autoryzuj**.

   Spowoduje to ukończenie konfiguracji domeny dla Microsoft 365.

## <a name="create-dns-records-with-manual-setup"></a>Tworzenie rekordów DNS z ręczną konfiguracją

Po dodaniu tych rekordów w usłudze GoDaddy domena zostanie skonfigurowana do pracy z usługi firmy Microsoft.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-a-txt-record-for-verification"></a>Dodawanie rekordu TXT w celu weryfikacji

Przed użyciem domeny z firmą Microsoft musimy upewnić się, że jesteś jej właścicielem. Możliwość zalogowania się do konta u rejestratora domen i utworzenia rekordu DNS potwierdza firmie Microsoft, że jesteś właścicielem domeny.

> [!NOTE]
> Ten rekord jest używany tylko do weryfikowania, że jesteś właścicielem domeny, i nie wywiera wpływu na nic innego. Jeśli chcesz, możesz go później usunąć.

1. Aby rozpocząć, przejdź do strony swoich domen w witrynie GoDaddy, używając [tego linku](https://account.godaddy.com/products/?go_redirect=disabled).

   Jeśli zostanie wyświetlony monit o zalogowanie się, użyj poświadczeń logowania, wybierz nazwę logowania w prawym górnym rogu, a następnie wybierz pozycję **Moje produkty**.

1. W obszarze Domeny wybierz trzy **kropki** obok domeny, którą chcesz zweryfikować, a następnie wybierz pozycję **Zarządzaj systemem DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Wybierz pozycję Zarządzaj systemem DNS z listy rozwijanej.":::

1. W obszarze **Rekordy** wybierz pozycję **DODAJ** (Może być konieczne przewinięcie w dół).

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Wybierz pozycję DODAJ.":::

1. Wybierz pozycję **TXT** z listy rozwijanej.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Wybierz pozycję TXT z listy rozwijanej Typ.":::

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z tabeli.

   |Wpisać|Host|Wartość TXT|Czas wygaśnięcia|
   |---|---|---|---|
   |TXT|@|MS=ms *XXXXXXXX*<br>**Uwaga**: jest to przykład. W tym miejscu użyj określonej wartości **Destination (Miejsce docelowe) lub Points to Address (Punkty do adresu** ) z tabeli . [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)|1 godzina  <br>|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXT-values.png" alt-text="Wypełnij wartości z tabeli rekordu TXT.":::

1. Wybierz **Zapisz**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXTSave.png" alt-text="Wybierz pozycję Zapisz.":::

   Przed kontynuowaniem poczekaj kilka minut na zaktualizowanie utworzonego właśnie rekordu w Internecie.

Po dodaniu rekordu w witrynie rejestratora domen wrócisz do firmy Microsoft i zażądasz rekordu. Gdy firma Microsoft znajdzie właściwy rekord TXT, domena zostanie zweryfikowana.
  
Aby zweryfikować rekord w Microsoft 365:
  
1. W centrum administracyjnym przejdź do **obszaru domeny Ustawienia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**.**</a>

1. Na stronie Domeny wybierz domenę, którą weryfikujesz, a następnie wybierz pozycję **Rozpocznij konfigurację**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Wybierz pozycję Rozpocznij konfigurację.":::

1. Wybierz pozycję **Kontynuuj**.
  
1. Na stronie **Weryfikowanie domeny** wybierz pozycję **Weryfikuj**.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Dodaj rekord MX, aby wiadomość e-mail dla twojej domeny przyszła do firmy Microsoft

1. Aby rozpocząć, przejdź do strony swoich domen w witrynie GoDaddy, używając [tego linku](https://account.godaddy.com/products/?go_redirect=disabled).

   Jeśli zostanie wyświetlony monit o zalogowanie się, użyj poświadczeń logowania, wybierz nazwę logowania w prawym górnym rogu, a następnie wybierz pozycję **Moje produkty**.

2. W obszarze Domeny wybierz trzy **kropki** obok domeny, którą chcesz zweryfikować, a następnie wybierz pozycję **Zarządzaj systemem DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Wybierz pozycję Zarządzaj systemem DNS z listy rozwijanej.":::

3. W obszarze **Rekordy** wybierz pozycję **DODAJ**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Wybierz pozycję DODAJ.":::

4. Wybierz **pozycję MX** z listy rozwijanej.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Wybierz pozycję MX z listy rozwijanej Typ.":::

5. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli.

   (Wybierz wartości **Typ** i **czas wygaśnięcia** z listy rozwijanej).

   |Wpisać|Host|Wskazuje na|Priority (Priorytet)|TTL (Czas wygaśnięcia)|
   |---|---|---|---|---|
   |MX|@| *\<domain-key\>*.mail.protection.outlook.com  <br/> **Uwaga:** Pobierz dane *\<domain-key\>* z konta Microsoft. [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)|10  <br/> Aby uzyskać więcej informacji o priorytetach, zobacz [Co to jest priorytet rekordu MX?](../setup/domains-faq.yml)|1 godzina|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Wypełnij wartości z tabeli rekordu MX.":::

6. Wybierz **Zapisz**.

### <a name="add-the-cname-record-required-for-microsoft"></a>Dodawanie rekordu CNAME wymaganego dla firmy Microsoft

1. Aby rozpocząć, przejdź do strony swoich domen w witrynie GoDaddy, używając [tego linku](https://account.godaddy.com/products/?go_redirect=disabled).

   Jeśli zostanie wyświetlony monit o zalogowanie się, użyj poświadczeń logowania, wybierz nazwę logowania w prawym górnym rogu, a następnie wybierz pozycję **Moje produkty**.

2. W obszarze Domeny wybierz trzy **kropki** obok domeny, którą chcesz zweryfikować, a następnie wybierz pozycję **Zarządzaj systemem DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Wybierz pozycję Zarządzaj systemem DNS z listy rozwijanej.":::

3. W obszarze **Rekordy** wybierz pozycję **DODAJ**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Wybierz pozycję DODAJ.":::

4. Wybierz pozycję **CNAME** z listy rozwijanej.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Wybierz pozycję CNAME z listy rozwijanej Typ.":::

5. Utwórz rekord CNAME.

   W polach nowego rekordu wpisz lub skopiuj i wklej wartości z pierwszego wiersza poniższej tabeli.

   (Wybierz wartość **czasu wygaśnięcia** z listy rozwijanej).

   |Wpisać|Host|Wskazuje na|Czas wygaśnięcia|
   |---|---|---|---|
   |CNAME|autodiscover|autodiscover.outlook.com|1 godzina|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="Wypełnij wartości z tabeli rekordu CNAME.":::

6. Wybierz **Zapisz**.

### <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Dodawanie rekordu TXT SPF w celu zapobiegania spamowi w wiadomościach e-mail

> [!IMPORTANT]
> Nie można mieć więcej niż jednego rekordu TXT na rekord SPF dla domeny. Jeśli domena ma więcej niż jeden rekord SPF, może to spowodować błędy poczty e-mail, a także problemy z dostarczaniem i klasyfikacją spamu. Jeśli masz już rekord SPF dla swojej domeny, nie twórz nowego rekordu dla firmy Microsoft. Zamiast tego dodaj wymagane wartości firmy Microsoft do bieżącego rekordu, aby mieć  *jeden*  rekord SPF zawierający oba zestawy wartości.

1. Aby rozpocząć, przejdź do strony swoich domen w witrynie GoDaddy, używając [tego linku](https://account.godaddy.com/products/?go_redirect=disabled).

   Jeśli zostanie wyświetlony monit o zalogowanie się, użyj poświadczeń logowania, wybierz nazwę logowania w prawym górnym rogu, a następnie wybierz pozycję **Moje produkty**.

2. W obszarze Domeny wybierz trzy **kropki** obok domeny, którą chcesz zweryfikować, a następnie wybierz pozycję **Zarządzaj systemem DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Wybierz pozycję Zarządzaj systemem DNS z listy rozwijanej.":::

3. W obszarze **Rekordy** wybierz pozycję **DODAJ**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Wybierz pozycję DODAJ.":::

4. Wybierz pozycję **TXT** z listy rozwijanej.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Wybierz pozycję TXT z listy rozwijanej Typ.":::

5. W polach nowego rekordu wpisz lub skopiuj i wklej następujące wartości.

   (Wybierz wartość **czasu wygaśnięcia** z list rozwijanych).

   |Wpisać|Host|Wartość TXT|Czas wygaśnięcia|
   |---|---|---|---|
   |TXT|@|v=spf1 include:spf.protection.outlook.com -all  <br/> **Uwaga:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostały poprawne.|1 godzina|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXT-values.png" alt-text="Wypełnij wartości z tabeli rekordu TXT.":::

6. Wybierz **Zapisz**.

## <a name="advanced-option-skype-for-business"></a>Opcja zaawansowana: Skype dla firm

Tę opcję należy wybrać tylko wtedy, gdy organizacja używa Skype dla firm dla usług komunikacji online, takich jak czat, połączenia konferencyjne i połączenia wideo, oprócz Microsoft Teams. Skype wymaga 4 rekordów: 2 rekordy SRV do komunikacji między użytkownikami i 2 rekordy CNAME, aby zalogować się i połączyć użytkowników z usługą.

### <a name="add-the-two-required-srv-records"></a>Dodawanie dwóch wymaganych rekordów SRV

1. Aby rozpocząć, przejdź do strony swoich domen w witrynie GoDaddy, używając [tego linku](https://account.godaddy.com/products/?go_redirect=disabled).

   Jeśli zostanie wyświetlony monit o zalogowanie się, użyj poświadczeń logowania, wybierz nazwę logowania w prawym górnym rogu, a następnie wybierz pozycję **Moje produkty**.

1. W obszarze Domeny wybierz trzy **kropki** obok domeny, którą chcesz zweryfikować, a następnie wybierz pozycję **Zarządzaj systemem DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Wybierz pozycję Zarządzaj systemem DNS z listy rozwijanej.":::

1. W obszarze **Rekordy** wybierz pozycję **DODAJ**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Wybierz pozycję DODAJ.":::

1. Wybierz pozycję **SRV** z listy rozwijanej.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Wybierz pozycję SRV z listy rozwijanej Typ.":::

1. Utwórz pierwszy rekord SRV.

   W polach nowego rekordu wpisz lub skopiuj i wklej wartości z pierwszego wiersza poniższej tabeli.

   (Wybierz wartości **Typ** i **Czas wygaśnięcia** z list rozwijanych).

   |Wpisać|Usługa|Protocol (Protokół)|Name (Nazwa)|Target (Element docelowy)|Priority (Priorytet)|Waga|Port|Czas wygaśnięcia|
   |---|---|---|---|---|---|---|---|---|
   |SRV|_sip|_tls|@|sipdir.online.lync.com|100| 1|443|1 godzina|
   |SRV|_sipfederationtls|_tcp|@| sipfed.online.lync.com| 100|1|5061|1 godzina|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-SRV-values.png" alt-text="Wypełnij wartości z tabeli rekordu SRV.":::

1. Wybierz **Zapisz**.

1. Dodaj inny rekord SRV, wybierając wartości z drugiego wiersza tabeli.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Dodaj dwa wymagane rekordy CNAME dla Skype dla firm
  
1. Aby rozpocząć, przejdź do strony swoich domen w witrynie GoDaddy, używając [tego linku](https://account.godaddy.com/products/?go_redirect=disabled).

   Jeśli zostanie wyświetlony monit o zalogowanie się, użyj poświadczeń logowania, wybierz nazwę logowania w prawym górnym rogu, a następnie wybierz pozycję **Moje produkty**.

1. W obszarze Domeny wybierz trzy **kropki** obok domeny, którą chcesz zweryfikować, a następnie wybierz pozycję **Zarządzaj systemem DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Wybierz pozycję Zarządzaj systemem DNS z listy rozwijanej.":::

1. W obszarze **Rekordy** wybierz pozycję **DODAJ**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Wybierz pozycję DODAJ.":::

1. Wybierz pozycję **CNAME** z listy rozwijanej.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Wybierz pozycję CNAME z listy rozwijanej Typ.":::

1. W pustych polach dla nowych rekordów wpisz lub skopiuj i wklej wartości z pierwszego wiersza w poniższej tabeli.

   |Wpisać|Host|Wskazuje na|Czas wygaśnięcia|
   |---|---|---|---|
   |CNAME|sip|sipdir.online.lync.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)**|1 godzina|
   |CNAME|lyncdiscover|webdir.online.lync.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)**|1 godzina|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="Wypełnij wartości z tabeli rekordu CNAME.":::
  
1. Wybierz **Zapisz**.
  
1. Dodaj inny rekord CNAME, wybierając wartości z drugiego wiersza tabeli.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Opcja zaawansowana: Intune i mobile Zarządzanie urządzeniami dla Microsoft 365

Ta usługa ułatwia zabezpieczanie i zdalne zarządzanie urządzeniami przenośnymi łączącymi się z domeną. Usługa Mobile Zarządzanie urządzeniami wymaga 2 rekordów CNAME, aby użytkownicy mogli rejestrować urządzenia w usłudze.

### <a name="add-the-two-required-cname-records-mobile-device-management"></a>Dodaj dwa wymagane rekordy CNAME Mobile Zarządzanie urządzeniami

1. Aby rozpocząć, przejdź do strony swoich domen w witrynie GoDaddy, używając [tego linku](https://account.godaddy.com/products/?go_redirect=disabled).

   Jeśli zostanie wyświetlony monit o zalogowanie się, użyj poświadczeń logowania, wybierz nazwę logowania w prawym górnym rogu, a następnie wybierz pozycję **Moje produkty**.

1. W obszarze Domeny wybierz trzy **kropki** obok domeny, którą chcesz zweryfikować, a następnie wybierz pozycję **Zarządzaj systemem DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Wybierz pozycję Zarządzaj systemem DNS z listy rozwijanej.":::

1. W obszarze **Rekordy** wybierz pozycję **DODAJ**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Wybierz pozycję DODAJ.":::

1. Wybierz pozycję **CNAME** z listy rozwijanej.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Wybierz pozycję CNAME z listy rozwijanej Typ.":::

1. W pustych polach dla nowych rekordów wpisz lub skopiuj i wklej wartości z pierwszego wiersza w poniższej tabeli.

   |Wpisać|Host|Wskazuje na|Czas wygaśnięcia|
   |---|---|---|---|
   |CNAME|enterpriseregistration|enterpriseregistration.windows.net.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)**|1 godzina|
   |CNAME|enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)**|1 godzina|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="Wypełnij wartości z tabeli rekordu CNAME.":::
  
1. Wybierz **Zapisz**.
  
1. Dodaj inny rekord CNAME, wybierając wartości z drugiego wiersza tabeli.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).
