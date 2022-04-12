---
title: Połączenie rekordy DNS w usłudze Cloudflare do Microsoft 365
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
description: Dowiedz się, jak zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, Skype dla firm Online i innych usług w witrynie Cloudflare for Microsoft.
ms.openlocfilehash: 164a681cccac3385d2ca963ac58706c8e743bc1e
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780374"
---
# <a name="connect-your-dns-records-at-cloudflare-to-microsoft-365"></a>Połączenie rekordy DNS w usłudze Cloudflare do Microsoft 365

 **[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji.

Jeśli cloudflare jest dostawcą hostingu DNS, wykonaj kroki opisane w tym artykule, aby zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, Skype dla firm Online itd.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Istnieją dwie opcje konfigurowania rekordów DNS dla domeny:

- [**Użyj Połączenie domeny**](#use-domain-connect-to-verify-and-set-up-your-domain) Jeśli nie skonfigurowano domeny z innym dostawcą usług poczty e-mail, wykonaj kroki Połączenie domeny, aby automatycznie zweryfikować i skonfigurować nową domenę do użycia z Microsoft 365.

    LUB

- [**Wykonaj kroki ręczne**](#create-dns-records-with-manual-setup) Zweryfikuj domenę, wykonując poniższe kroki ręcznie, i wybierz, kiedy i które rekordy należy dodać do rejestratora domeny. Dzięki temu można skonfigurować nowe rekordy MX (poczty e-mail), na przykład dla Twojej wygody.

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>Weryfikowanie i konfigurowanie domeny przy użyciu Połączenie domeny

Wykonaj następujące kroki, aby automatycznie zweryfikować i skonfigurować domenę Cloudflare przy użyciu Microsoft 365:

1. W Centrum administracyjne platformy Microsoft 365 wybierz pozycję **Ustawienia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domeny**</a>, a następnie wybierz domenę, którą chcesz skonfigurować.

1. Wybierz trzy kropki (więcej akcji) \> wybierz pozycję **Rozpocznij konfigurację**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Wybierz pozycję Rozpocznij konfigurację.":::

1. Na stronie Jak chcesz połączyć domenę? wybierz pozycję **Kontynuuj**.

1. Na stronie Dodawanie rekordów DNS wybierz pozycję **Dodaj rekordy DNS**.

1. Na stronie logowania cloudflare zaloguj się do swojego konta, a następnie wybierz pozycję **Autoryzuj**.

    Spowoduje to ukończenie konfiguracji domeny dla Microsoft 365.

## <a name="create-dns-records-with-manual-setup"></a>Tworzenie rekordów DNS z ręczną konfiguracją

Po dodaniu tych rekordów w usłudze Cloudflare domena zostanie skonfigurowana do pracy z usługami Microsoft 365.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="change-your-domains-nameserver-ns-records"></a>Zmienianie rekordów serwerów nazw domeny (SN)

> [!IMPORTANT]
> Tę procedurę należy wykonać w witrynie rejestratora domen, u którego kupiono i zarejestrowano domenę.

Po zarejestrowaniu się w usłudze Cloudflare dodano domenę przy użyciu procesu konfiguracji cloudflare.

Dodana domena została zakupiona od cloudflare lub osobnego rejestratora domen. Aby zweryfikować i utworzyć rekordy DNS dla domeny w Microsoft 365, należy najpierw zmienić serwery nazw u rejestratora domen, tak aby używały serwerów nazw Cloudflare.

Aby samodzielnie zmienić serwery nazw domen w witrynie sieci Web rejestratora domen, wykonaj poniższe czynności.

1. Znajdź obszar w witrynie sieci Web rejestratora domen, w którym można edytować serwery nazw dla Twojej domeny.

2. Utwórz dwa rekordy programu nameserver przy użyciu wartości w poniższej tabeli lub edytuj istniejące rekordy serwera nazw, aby były zgodne z tymi wartościami.

    |Wpisać|Value|
    |---|---|
    |Pierwszy serwer nazw|Użyj wartości elementu nazw dostarczonej przez usługę Cloudflare.|
    |Drugi serwer nazw|Użyj wartości elementu nazw dostarczonej przez usługę Cloudflare.|

    > [!TIP]
    > Należy użyć co najmniej dwóch rekordów serwera nazw. Jeśli na liście znajdują się inne serwery nazw, należy je usunąć.

3. Zapisz zmiany.

> [!NOTE]
> Aktualizowanie rekordu serwera nazw w internetowym systemie DNS może potrwać nawet kilka godzin. Następnie poczta e-mail firmy Microsoft i inne usługi zostaną ustawione do pracy z Domeną.

### <a name="add-a-txt-record-for-verification"></a>Dodawanie rekordu TXT w celu weryfikacji

Przed użyciem domeny z firmą Microsoft musimy upewnić się, że jesteś jej właścicielem. Możliwość zalogowania się do konta u rejestratora domen i utworzenia rekordu DNS potwierdza firmie Microsoft, że jesteś właścicielem domeny.

> [!NOTE]
> Ten rekord jest używany tylko do weryfikowania, że jesteś właścicielem domeny, i nie wywiera wpływu na nic innego. Jeśli chcesz, możesz go później usunąć.

1. Aby rozpocząć, przejdź do strony domen w witrynie Cloudflare, korzystając z [tego linku](https://www.cloudflare.com/a/login). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie głównej wybierz domenę, którą chcesz zaktualizować.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Wybierz domenę, którą chcesz zaktualizować.":::

1. Na stronie Przegląd domeny wybierz pozycję **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Wybierz pozycję DNS.":::

1. Na stronie zarządzania DNS wybierz pozycję **+Dodaj rekord**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Wybierz pozycję Dodaj rekord.":::

1. Wybierz typ TXT z listy rozwijanej, a następnie wpisz lub skopiuj i wklej wartości z tej tabeli.

    |Wpisać|Name (Nazwa)|Czas wygaśnięcia|Zawartość|
    |---|---|---|:----|
    |TXT|@|30 minut|MS=*msXXXXXXXXXX* <br/> **Uwaga:** Jest to przykład. W tym miejscu użyj określonej wartości **Destination (Miejsce docelowe) lub Points to Address (Punkty do adresu** ) z tabeli . [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)|

1. Wybierz **Zapisz**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-TXT-save.png" alt-text="Wybierz pozycję Dodaj rekord.":::

   Przed kontynuowaniem poczekaj kilka minut na zaktualizowanie utworzonego właśnie rekordu w Internecie.

Po dodaniu rekordu w witrynie rejestratora domen wrócisz do firmy Microsoft i wyszukasz rekord. Gdy firma Microsoft znajdzie właściwy rekord TXT, domena zostanie zweryfikowana.

Aby zweryfikować rekord w Microsoft 365:

1. W centrum administracyjnym przejdź do **obszaru domeny Ustawienia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**.**</a>

1. Na stronie Domeny wybierz domenę, którą weryfikujesz, a następnie wybierz pozycję **Rozpocznij konfigurację**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Wybierz pozycję Rozpocznij konfigurację.":::

1. Wybierz pozycję **Kontynuuj**.

1. Na stronie **Weryfikowanie domeny** wybierz pozycję **Weryfikuj**.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Dodaj rekord MX, aby wiadomość e-mail dla twojej domeny przyszła do firmy Microsoft

1. Aby rozpocząć, przejdź do strony domen w witrynie Cloudflare, korzystając z [tego linku](https://www.cloudflare.com/a/login). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie głównej wybierz domenę, którą chcesz zaktualizować.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Wybierz domenę, którą chcesz zaktualizować.":::

1. Na stronie Przegląd domeny wybierz pozycję **DNS**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Wybierz pozycję DNS.":::

1. Na stronie zarządzania DNS wybierz pozycję **+Dodaj rekord**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Wybierz pozycję Dodaj rekord.":::

1. Wybierz typ MX z listy rozwijanej, a następnie wpisz lub skopiuj i wklej wartości z tej tabeli.

   |Wpisać|Name (Nazwa)|Serwer poczty|Czas wygaśnięcia|Priority (Priorytet)|
   |---|---|---|---|---|
   |MX|@|*\<domain-key\>*.mail.protection.outlook.com <br/> **Uwaga:** Pobierz dane *\<domain-key\>* z konta Microsoft 365. [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)|30 minut|1 <br/> Aby uzyskać więcej informacji o priorytetach, zobacz [Co to jest priorytet rekordu MX?](../setup/domains-faq.yml) <br/>|

1. Wybierz **Zapisz**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-mx-save.png" alt-text="Wybierz pozycję Dodaj rekord.":::

1. Jeśli w sekcji **Rekordy MX** znajdują się inne rekordy MX, usuń je, wybierając pozycję **Edytuj**, a następnie wybierz pozycję **Usuń**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-mx-delete.png" alt-text="Wybierz pozycję Usuń.":::

1. W oknie dialogowym potwierdzenia wybierz pozycję **Usuń** , aby potwierdzić zmiany.

### <a name="add-the-cname-record-required-for-microsoft"></a>Dodawanie rekordu CNAME wymaganego dla firmy Microsoft

1. Aby rozpocząć, przejdź do strony domen w witrynie Cloudflare, korzystając z [tego linku](https://www.cloudflare.com/a/login). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie głównej wybierz domenę, którą chcesz zaktualizować.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Wybierz domenę, którą chcesz zaktualizować.":::

1. Na stronie Przegląd domeny wybierz pozycję **DNS**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Wybierz pozycję DNS.":::

1. Na stronie **zarządzania DNS** wybierz pozycję **+Dodaj rekord**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Wybierz pozycję Dodaj rekord.":::

1. Wybierz typ CNAME z listy rozwijanej, a następnie wpisz lub skopiuj i wklej wartości z tej tabeli.

    |Wpisać|Name (Nazwa)|Target (Element docelowy)|Czas wygaśnięcia|
    |---|---|---|---|
    |CNAME|autodiscover|autodiscover.outlook.com|Automatycznie|

1. Wybierz **Zapisz**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="Wybierz pozycję Zapisz.":::

### <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Dodawanie rekordu TXT SPF w celu zapobiegania spamowi w wiadomościach e-mail

> [!IMPORTANT]
> Nie można mieć więcej niż jednego rekordu TXT na rekord SPF dla domeny. Jeśli domena ma więcej niż jeden rekord SPF, może to spowodować błędy poczty e-mail, a także problemy z dostarczaniem i klasyfikacją spamu. Jeśli masz już rekord SPF dla domeny, nie należy tworzyć nowego rekordu dla Microsoft 365. Zamiast tego dodaj wymagane wartości Microsoft 365 do bieżącego rekordu, aby mieć *jeden* rekord SPF zawierający oba zestawy wartości.

1. Aby rozpocząć, przejdź do strony domen w witrynie Cloudflare, korzystając z [tego linku](https://www.cloudflare.com/a/login). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie głównej wybierz domenę, którą chcesz zaktualizować.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Wybierz domenę, którą chcesz zaktualizować.":::

1. Na stronie Przegląd domeny wybierz pozycję **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Wybierz pozycję DNS.":::

1. Na stronie zarządzania DNS wybierz pozycję **+Dodaj rekord**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Wybierz pozycję Dodaj rekord.":::

1. Wybierz typ TXT z listy rozwijanej, a następnie wpisz lub skopiuj i wklej wartości z tej tabeli.

    |Wpisać|Name (Nazwa)|Czas wygaśnięcia|Zawartość|
    |---|---|---|---|
    |TXT|@|30 minut|v=spf1 include:spf.protection.outlook.com -all <br/> **Uwaga:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostały poprawne.|

1. Wybierz **Zapisz**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-TXT-save.png" alt-text="Wybierz pozycję Zapisz.":::

## <a name="advanced-option-skype-for-business"></a>Opcja zaawansowana: Skype dla firm

Tę opcję należy wybrać tylko wtedy, gdy organizacja używa Skype dla firm dla usług komunikacji online, takich jak czat, połączenia konferencyjne i połączenia wideo, oprócz Microsoft Teams. Skype wymaga 4 rekordów: 2 rekordy SRV do komunikacji między użytkownikami i 2 rekordy CNAME, aby zalogować się i połączyć użytkowników z usługą.

### <a name="add-the-two-required-srv-records"></a>Dodawanie dwóch wymaganych rekordów SRV

> [!IMPORTANT]
> Należy pamiętać, że usługa Cloudflare jest odpowiedzialna za udostępnienie tej funkcji. W przypadku wystąpienia rozbieżności między poniższymi krokami a bieżącym graficznym interfejsem użytkownika Cloudflare (Graficzny interfejs użytkownika) skorzystaj z [Community Cloudflare](https://community.cloudflare.com/).

1. Aby rozpocząć, przejdź do strony domen w witrynie Cloudflare, korzystając z [tego linku](https://www.cloudflare.com/a/login). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie głównej wybierz domenę, którą chcesz zaktualizować.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Wybierz domenę, którą chcesz zaktualizować.":::

1. Na stronie Przegląd domeny wybierz pozycję **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Wybierz pozycję DNS.":::

1. Na stronie zarządzania DNS wybierz pozycję **+Dodaj rekord**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Wybierz pozycję Dodaj rekord.":::

1. Wybierz typ SRV z listy rozwijanej, a następnie wpisz lub skopiuj i wklej wartości z tej tabeli.

    |Wpisać|Name (Nazwa)|Usługa|Protocol (Protokół)|Czas wygaśnięcia|Priority (Priorytet)|Waga|Port|Target (Element docelowy)|
    |---|---|---|---|---|---|---|---|---|
    |SRV|Użyj *domain_name*; na przykład contoso.com|_sip|TLS|30 minut|100|1|443|sipfed.online.lync.com|
    |SRV|_sipfederationtls|TCP|Użyj *domain_name*; na przykład contoso.com|30 minut|100|1|5061|sipfed.online.lync.com|

1. Wybierz **Zapisz**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-srv-save.png" alt-text="Wybierz pozycję Zapisz.":::

1. Dodaj inny rekord SRV, kopiując wartości z drugiego wiersza tabeli.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Dodaj dwa wymagane rekordy CNAME dla Skype dla firm

1. Aby rozpocząć, przejdź do strony domen w witrynie Cloudflare, korzystając z [tego linku](https://www.cloudflare.com/a/login). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie głównej wybierz domenę, którą chcesz zaktualizować.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Wybierz domenę, którą chcesz zaktualizować.":::

1. Na stronie Przegląd domeny wybierz pozycję **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Wybierz pozycję DNS.":::

1. Na stronie zarządzania DNS wybierz pozycję **+Dodaj rekord**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Wybierz pozycję Dodaj rekord.":::

1. Wybierz typ CNAME z listy rozwijanej, a następnie wpisz lub skopiuj i wklej wartości z tej tabeli.

    |Wpisać|Name (Nazwa)|Target (Element docelowy)|Czas wygaśnięcia|
    |---|---|---|---|
    |CNAME|sip|sipdir.online.lync.com. <br/> **Wartość ta MUSI mieć na końcu kropkę (.)**|1 godzina|
    |CNAME|lyncdiscover|webdir.online.lync.com. <br/> **Wartość ta MUSI mieć na końcu kropkę (.)**|1 godzina|

1. Wybierz pozycję **Zapisz**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="Wybierz pozycję Zapisz.":::

1. Dodaj inny rekord CNAME, kopiując wartości z drugiego wiersza tabeli.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Opcja zaawansowana: Intune i mobile Zarządzanie urządzeniami dla Microsoft 365

Ta usługa ułatwia zabezpieczanie i zdalne zarządzanie urządzeniami przenośnymi łączącymi się z domeną. Usługa Mobile Zarządzanie urządzeniami wymaga 2 rekordów CNAME, aby użytkownicy mogli rejestrować urządzenia w usłudze.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Dodaj dwa wymagane rekordy CNAME dla usługi Mobile Zarządzanie urządzeniami

1. Aby rozpocząć, przejdź do strony domen w witrynie Cloudflare, korzystając z [tego linku](https://www.cloudflare.com/a/login). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie głównej wybierz domenę, którą chcesz zaktualizować.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Wybierz domenę, którą chcesz zaktualizować.":::

1. Na stronie Przegląd domeny wybierz pozycję **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Wybierz pozycję DNS.":::

1. Na stronie zarządzania DNS wybierz pozycję **+Dodaj rekord**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Wybierz pozycję Dodaj rekord.":::

1. Wybierz typ CNAME z listy rozwijanej, a następnie wpisz lub skopiuj i wklej wartości z tej tabeli.

    |Wpisać|Name (Nazwa)|Target (Element docelowy)|Czas wygaśnięcia|
    |---|---|---|---|
    |CNAME|enterpriseregistration|enterpriseregistration.windows.net. <br/> **Wartość ta MUSI mieć na końcu kropkę (.)**|1 godzina|
    |CNAME|enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com. <br/> **Wartość ta MUSI mieć na końcu kropkę (.)**|1 godzina|

1. Wybierz **Zapisz**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="Wybierz pozycję Zapisz.":::

1. Dodaj inny rekord CNAME, kopiując wartości z drugiego wiersza tabeli.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).
