---
title: Łączenie rekordów DNS w 123-reg.co.uk z platformą Microsoft 365
f1.keywords:
- CSH
ms.author: efrene
author: efrene
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
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 1f2d08c9-2a88-4d2f-ae1f-e39f9e358b17
description: Dowiedz się, jak zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, Skype dla firm Online i innych usług w 123-reg.co.uk dla firmy Microsoft.
ms.openlocfilehash: 97a00c046f467dd4ced4c63a4cbfc8114d06d2dd
ms.sourcegitcommit: 8cd230e243eba452b27f725d66152becb6aff49b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2022
ms.locfileid: "66563412"
---
# <a name="connect-your-dns-records-at-123-regcouk-to-microsoft-365"></a>Łączenie rekordów DNS w 123-reg.co.uk z platformą Microsoft 365

 **[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji.

Jeśli witryna 123-reg.co.uk jest Twoim dostawcą hostingu DNS, wykonaj czynności opisane w tym artykule, aby zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, usługi Skype dla firm Online itp.

Po dodaniu tych rekordów w 123-reg.co.uk domena zostanie skonfigurowana do pracy z usługami firmy Microsoft.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli masz problemy z przepływem poczty lub inne problemy po dodaniu rekordów DNS, zobacz [Znajdowanie i rozwiązywanie problemów po dodaniu domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-a-txt-record-for-verification"></a>Dodawanie rekordu TXT w celu weryfikacji

Przed użyciem domeny z firmą Microsoft musimy upewnić się, że jesteś jej właścicielem. Możliwość zalogowania się do konta u rejestratora domen i utworzenia rekordu DNS potwierdza firmie Microsoft, że jesteś właścicielem domeny.

> [!NOTE]
> Ten rekord jest używany tylko do weryfikowania, że jesteś właścicielem domeny, i nie wywiera wpływu na nic innego. Jeśli chcesz, możesz go później usunąć.

1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie 123-reg.co.uk, używając [tego linku](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Zostanie wyświetlony monit o zalogowanie się.

2. Wybierz pozycję **Domeny**, a następnie na stronie Przegląd nazwy domeny wybierz nazwę domeny, którą chcesz zweryfikować, lub przejdź do panelu sterowania.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Wybierz domenę, którą chcesz zweryfikować.":::

3. Na stronie Zarządzanie domeną w obszarze **Zaawansowane ustawienia domeny** wybierz pozycję **Zarządzaj usługą DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Wybierz pozycję Zarządzaj systemem DNS z listy rozwijanej.":::

4. Na stronie Zarządzanie systemem DNS wybierz kartę **Zaawansowany system DNS** .

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Wybierz kartę Zaawansowany system DNS.":::

5. W polu **Typ** nowego rekordu wybierz pozycję **TXT/SPF** z listy rozwijanej, a następnie wpisz lub skopiuj i wklej inne wartości z poniższej tabeli.

    |Hostname (Nazwa hosta)|Type (Typ)|Destination TXT/SPF (TXT/SPF miejsca docelowego)|
    |---|---|---|
    |@|TXT/SPF|MS=ms *XXXXXXXXXX* <br/> **Uwaga:** Jest to przykład. W tym miejscu użyj określonej wartości **Destination (Miejsce docelowe) lub Points to Address (Punkty do adresu** ) z tabeli . [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="Wybierz typ TXT/SPF z listy rozwijanej i wypełnij wartości.":::

6. Wybierz opcję **Dodaj**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TXTSPF-Add.png" alt-text="Wybierz pozycję Dodaj.":::

   Przed kontynuowaniem poczekaj kilka minut na zaktualizowanie utworzonego właśnie rekordu w Internecie.

Po dodaniu rekordu w witrynie rejestratora domen wrócisz do firmy Microsoft i zażądasz wyszukania rekordu. Gdy firma Microsoft znajdzie właściwy rekord TXT, domena zostanie zweryfikowana.

Aby zweryfikować rekord w usłudze Microsoft 365:

1. W centrum administracyjnym przejdź do obszaru **Domeny ustawień**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank"></a>

1. Na stronie Domeny wybierz domenę, którą weryfikujesz, a następnie wybierz pozycję **Rozpocznij konfigurację**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Wybierz pozycję Rozpocznij konfigurację.":::

1. Naciśnij przycisk **Kontynuuj**.

1. Na stronie **Weryfikowanie domeny** wybierz pozycję **Weryfikuj**.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Dodaj rekord MX, aby wiadomość e-mail dla twojej domeny przyszła do firmy Microsoft

1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie 123-reg.co.uk, używając [tego linku](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Zostanie wyświetlony monit o zalogowanie się.

2. Na stronie Domain name overview (Przegląd nazw domen) wybierz nazwę domeny, którą chcesz edytować.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Wybierz nazwę domeny, którą chcesz edytować.":::

3. Na stronie Zarządzanie domeną w obszarze **Zaawansowane ustawienia domeny** wybierz pozycję **Zarządzaj usługą DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Wybierz pozycję Zarządzaj systemem DNS z listy rozwijanej.":::

4. Na stronie Zarządzanie systemem DNS wybierz kartę **Zaawansowany system DNS** .

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Wybierz kartę Zaawansowany system DNS.":::

5. W polu **Typ** nowego rekordu wybierz pozycję **MX** z listy rozwijanej, a następnie wpisz lub skopiuj i wklej inne wartości z poniższej tabeli.

    |Hostname (Nazwa hosta)|Type (Typ)|Priority (Priorytet)|Destination MX (MX miejsca docelowego)|
    |---|---|---|---|
    |@|MX|1 <br/> Aby uzyskać więcej informacji o priorytetach, zobacz [Co to jest priorytet rekordu MX?](../setup/domains-faq.yml)|*\<domain-key\>*.mail.protection.outlook.com. <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> **Uwaga:** Pobierz dane \<domain-key\> z konta Microsoft. [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX.png" alt-text="Wybierz typ MX z listy rozwijanej i wypełnij wartości.":::

6. Wybierz opcję **Dodaj**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX-Add.png" alt-text="Wybierz pozycję Dodaj.":::

7. Jeśli istnieją inne rekordy MX, usuń je, wybierając ikonę **Usuń (kosz na śmieci)** dla tego rekordu.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX-delete.png" alt-text="Wybierz pozycję Usuń (kosz na śmieci).":::

## <a name="add-the-cname-record-required-for-microsoft"></a>Dodawanie rekordu CNAME wymaganego dla firmy Microsoft

1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie 123-reg.co.uk, używając [tego linku](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Zostanie wyświetlony monit o zalogowanie się.

2. Na stronie Domain name overview (Przegląd nazw domen) wybierz nazwę domeny, którą chcesz edytować.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Wybierz nazwę domeny, którą chcesz edytować.":::

3. Na stronie Zarządzanie domeną w obszarze **Zaawansowane ustawienia domeny** wybierz pozycję **Zarządzaj usługą DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Wybierz pozycję Zarządzaj systemem DNS z listy rozwijanej.":::

4. Na stronie Zarządzanie systemem DNS wybierz kartę **Zaawansowany system DNS** .

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Wybierz kartę Zaawansowany system DNS.":::

5. Dodaj rekord CNAME.

    W polu **Typ** nowego rekordu wybierz pozycję **CNAME** z listy rozwijanej, a następnie wpisz lub skopiuj i wklej inne wartości z poniższej tabeli.

    |Hostname (Nazwa hosta)|Type (Typ)|Destination CNAME (CNAME miejsca docelowego)|
    |---|---|---|
    |autodiscover|CNAME|autodiscover.outlook.com. <br/> **Wartość ta MUSI mieć na końcu kropkę (.)**|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="Wybierz typ CNAME z listy rozwijanej i wypełnij wartości.":::

6. Wybierz opcję **Dodaj**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="Wybierz pozycję Dodaj.":::

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Dodawanie rekordu TXT SPF w celu zapobiegania spamowi w wiadomościach e-mail

> [!IMPORTANT]
> Nie można mieć więcej niż jednego rekordu TXT na rekord SPF dla domeny. Jeśli domena ma więcej niż jeden rekord SPF, może to spowodować błędy poczty e-mail, a także problemy z dostarczaniem i klasyfikacją spamu. Jeśli masz już rekord SPF dla domeny, nie twórz nowego rekordu dla aplikacji Microsfot. Zamiast tego dodaj wymagane wartości firmy Microsoft do bieżącego rekordu, aby mieć *jeden* rekord SPF zawierający oba zestawy wartości. Potrzebujesz przykładów? Zapoznaj się z tymi [rekordami systemu nazw domen zewnętrznych dla firmy Microsoft](../../enterprise/external-domain-name-system-records.md). Do zweryfikowania rekordu SPF możesz użyć jednego z następujących [narzędzi do weryfikowania rekordu SPF](../setup/domains-faq.yml).

1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie 123-reg.co.uk, używając [tego linku](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Zostanie wyświetlony monit o zalogowanie się.

2. Na stronie Domain name overview (Przegląd nazw domen) wybierz nazwę domeny, którą chcesz edytować.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Wybierz nazwę domeny, którą chcesz edytować.":::

3. Na stronie Zarządzanie domeną w obszarze **Zaawansowane ustawienia domeny** wybierz pozycję **Zarządzaj usługą DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Wybierz pozycję Zarządzaj systemem DNS z listy rozwijanej.":::

4. Na stronie Zarządzanie systemem DNS wybierz kartę **Zaawansowany system DNS** .

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Wybierz kartę Zaawansowany system DNS.":::

5. W polu **Typ** nowego rekordu wybierz pozycję **TXT/SPF** z listy rozwijanej, a następnie wpisz lub skopiuj i wklej inne wartości z poniższej tabeli.

    |Hostname (Nazwa hosta)|Type (Typ)|Destination TXT/SPF (TXT/SPF miejsca docelowego)|
    |---|---|---|
    |@|TXT/SPF|v=spf1 include:spf.protection.outlook.com -all <br/> **Uwaga:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostały poprawne.|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="Wybierz typ TXT/SPF z listy rozwijanej i wypełnij wartości.":::

6. Wybierz opcję **Dodaj**.

## <a name="advanced-option-skype-for-business"></a>Opcja zaawansowana: Skype dla firm

Tę opcję należy wybrać tylko wtedy, gdy organizacja używa Skype dla firm dla usług komunikacji online, takich jak czat, połączenia konferencyjne i połączenia wideo, oprócz usługi Microsoft Teams. Skype potrzebuje 4 rekordów: 2 rekordy SRV do komunikacji między użytkownikami i 2 rekordy CNAME, aby zalogować się i połączyć użytkowników z usługą.

### <a name="add-the-two-required-srv-records"></a>Dodawanie dwóch wymaganych rekordów SRV

1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie 123-reg.co.uk, używając [tego linku](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Zostanie wyświetlony monit o zalogowanie się.

2. Na stronie Domain name overview (Przegląd nazw domen) wybierz nazwę domeny, którą chcesz edytować.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Wybierz nazwę domeny, którą chcesz edytować.":::

3. Na stronie Zarządzanie domeną w obszarze **Zaawansowane ustawienia domeny** wybierz pozycję **Zarządzaj usługą DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Wybierz pozycję Zarządzaj systemem DNS z listy rozwijanej.":::

4. Na stronie Zarządzanie systemem DNS wybierz kartę **Zaawansowany system DNS** .

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Wybierz kartę Zaawansowany system DNS.":::

5. Dodaj pierwszy z dwóch rekordów SRV:

   W polu **Typ** nowego rekordu wybierz pozycję **SRV** z listy rozwijanej, a następnie wpisz lub skopiuj i wklej inne wartości z poniższej tabeli.

    |Hostname (Nazwa hosta)|Type (Typ)|Priority (Priorytet)|TTL (Czas wygaśnięcia)|Destination SRV (SRV miejsca docelowego)|
    |---|---|---|---|---|
    |_sip._tls|SRV|100|3600|1 443 sipdir.online.lync.com. **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> **Uwaga:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostały poprawne.|
    |_sipfederationtls._tcp|SRV|100|3600|1 5061 sipfed.online.lync.com. **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> **Uwaga:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostały poprawne.|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="Wybierz typ TXT/SPF z listy rozwijanej i wypełnij wartości.":::

6. Wybierz opcję **Dodaj**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TXTSPF-Add.png" alt-text="Wybierz pozycję Dodaj.":::

7. Dodaj drugi rekord SRV.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli masz problemy z przepływem poczty lub inne problemy po dodaniu rekordów DNS, zobacz [Znajdowanie i rozwiązywanie problemów po dodaniu domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Dodaj dwa wymagane rekordy CNAME dla Skype dla firm

1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie 123-reg.co.uk, używając [tego linku](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie Domain name overview (Przegląd nazw domen) wybierz nazwę domeny, którą chcesz edytować.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Wybierz nazwę domeny, którą chcesz edytować.":::

1. Na stronie Zarządzanie domeną w obszarze **Zaawansowane ustawienia domeny** wybierz pozycję **Zarządzaj usługą DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Wybierz pozycję Zarządzaj systemem DNS z listy rozwijanej.":::

1. Na stronie Zarządzanie systemem DNS wybierz kartę **Zaawansowany system DNS** .

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Wybierz kartę Zaawansowany system DNS.":::

1. Dodaj pierwszy rekord CNAME.

    W polu **Typ** nowego rekordu wybierz pozycję **CNAME** z listy rozwijanej, a następnie wpisz lub skopiuj i wklej inne wartości z poniższej tabeli.

    |Hostname (Nazwa hosta)|Type (Typ)|Destination CNAME (CNAME miejsca docelowego)|
    |---|---|---|
    |sip|CNAME|sipdir.online.lync.com. <br/> **Wartość ta MUSI mieć na końcu kropkę (.)**|
    |lyncdiscover|CNAME|webdir.online.lync.com. <br/> **Wartość ta MUSI mieć na końcu kropkę (.)**|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="Wybierz typ CNAME z listy rozwijanej i wypełnij wartości.":::

1. Wybierz opcję **Dodaj**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="Wybierz pozycję Dodaj.":::

1. Dodaj inny rekord CNAME.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Opcja zaawansowana: Intune i mobile Zarządzanie urządzeniami dla platformy Microsoft 365

Ta usługa ułatwia zabezpieczanie i zdalne zarządzanie urządzeniami przenośnymi łączącymi się z domeną. Usługa Mobile Zarządzanie urządzeniami wymaga dwóch rekordów CNAME, aby użytkownicy mogli rejestrować urządzenia w usłudze.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Dodaj dwa wymagane rekordy CNAME dla usługi Mobile Zarządzanie urządzeniami

1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie 123-reg.co.uk, używając [tego linku](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie Domain name overview (Przegląd nazw domen) wybierz nazwę domeny, którą chcesz edytować.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Wybierz nazwę domeny, którą chcesz edytować.":::

1. Na stronie Zarządzanie domeną w obszarze **Zaawansowane ustawienia domeny** wybierz pozycję **Zarządzaj usługą DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Wybierz pozycję Zarządzaj systemem DNS z listy rozwijanej.":::

1. Na stronie Zarządzanie systemem DNS wybierz kartę **Zaawansowany system DNS** .

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Wybierz kartę Zaawansowany system DNS.":::

1. Dodaj pierwszy rekord CNAME.

    W polu **Typ** nowego rekordu wybierz pozycję **CNAME** z listy rozwijanej, a następnie wpisz lub skopiuj i wklej inne wartości z poniższej tabeli.

   |Hostname (Nazwa hosta)|Type (Typ)|Destination CNAME (CNAME miejsca docelowego)|
   |---|---|---|
   |enterpriseregistration|CNAME|enterpriseregistration.windows.net. <br/> **Wartość ta MUSI mieć na końcu kropkę (.)**|
   |enterpriseenrollment|CNAME|enterpriseenrollment.manage.microsoft.com. <br/> **Wartość ta MUSI mieć na końcu kropkę (.)**|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="Wybierz typ CNAME z listy rozwijanej i wypełnij wartości.":::

1. Wybierz opcję **Dodaj**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="Wybierz pozycję Dodaj.":::

1. Dodaj inny rekord CNAME.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).
