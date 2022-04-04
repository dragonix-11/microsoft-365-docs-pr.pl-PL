---
title: Połączenie rekordy DNS w witrynie web.com Microsoft 365
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
description: Dowiedz się, jak zweryfikować domenę i skonfigurować rekordy DNS dla poczty e Skype dla firm online i innych usług w witrynie web.com firmy Microsoft.
ms.openlocfilehash: 612c22b518402fccaf9ced76b2506aa15c0e89f6
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2022
ms.locfileid: "64568417"
---
# <a name="connect-your-dns-records-at-webcom-to-microsoft-365"></a>Połączenie rekordy DNS w witrynie web.com Microsoft 365

 **[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji.

Jeśli web.com hostingu DNS, wykonaj czynności opisane w tym artykule, aby zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, dla usługi Skype dla firm Online itp.

Po dodaniu tych rekordów web.com Twoja domena będzie skonfigurować do współpracy z usługi firmy Microsoft.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="change-your-domains-nameserver-ns-records"></a>Zmienianie rekordów serwerów nazw domeny (SN)

> [!IMPORTANT]
> Tę procedurę należy wykonać w witrynie rejestratora domen, u którego kupiono i zarejestrowano domenę.

Podczas tworzenia konta w web.com dodano domenę przy użyciu procesu konfiguracji web.com **konta** .

Aby zweryfikować i utworzyć rekordy DNS dla Twojej domeny w firmie Microsoft, musisz najpierw zmienić serwery nazw u rejestratora domen, tak aby używały web.com nazw.

Aby samodzielnie zmienić serwery nazw domen w witrynie sieci Web rejestratora domen, wykonaj poniższe czynności.

1. Znajdź obszar w witrynie sieci Web rejestratora domen, w którym można edytować serwery nazw dla Twojej domeny.

2. Utwórz dwa rekordy serwera nazw, używając wartości z poniższej tabeli, lub edytuj istniejące rekordy serwera nazw tak, aby były zgodne z tymi wartościami.

    |Wpisać|Value|
    |---|---|
    |Pierwszy serwer nazw|Użyj wartości serwera nazw podanej przez web.com.|
    |Drugi serwer nazw|Użyj wartości serwera nazw podanej przez web.com.|

    > [!TIP]
    > Należy użyć co najmniej dwóch rekordów serwera nazw. Jeśli na liście znajdują się jakiekolwiek inne serwery nazw, należy je usunąć.

3. Zapisz zmiany.

> [!NOTE]
> Aktualizowanie rekordu serwera nazw w internetowym systemie DNS może potrwać nawet kilka godzin. Wtedy poczta e-mail Firmy Microsoft i inne usługi będą ustawione do współpracy z Twoją domeną.

## <a name="add-a-txt-record-for-verification"></a>Dodawanie rekordu TXT w celu weryfikacji

Zanim będziecie używać własnej domeny z firmą Microsoft, musimy się upewnić, że jesteś jej właścicielem. Możliwość zalogowania się do swojego konta w witrynie rejestratora domen i utworzenia rekordu DNS udowadnia firmie Microsoft, że jesteś właścicielem domeny.

> [!NOTE]
> Ten rekord jest używany tylko do weryfikowania, że jesteś właścicielem domeny, i nie wywiera wpływu na nic innego. Jeśli chcesz, możesz go później usunąć.

1. Aby rozpocząć pracę, przejdź do swojej strony domen w web.com, używając [tego linku](https://checkout.web.com/manage-it/index.jsp). Zaloguj się najpierw.

1. Na stronie docelowej wybierz pozycję **Domain Names (Nazwy domen**).

1. W **obszarze** Akcje wybierz trzy kropki, a następnie z  listy rozwijanej wybierz pozycję Zarządzaj.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Z listy rozwijanej wybierz pozycję Zarządzaj.":::

1. Przewiń w dół, aby **wybrać pozycję Narzędzia zaawansowane**, a następnie obok **przycisku Advanced DNS Records (Zaawansowane rekordy DNS**) wybierz pozycję **MANAGE (ZARZĄDZAJ**).

    Może być konieczne wybranie **przycisku Continue (Kontynuuj** ), aby uzyskać dostęp do strony Manage Advanced DNS Records (Zarządzanie zaawansowanymi rekordami DNS).

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Obok przycisku Advanced DNS records (Zaawansowane rekordy DNS) wybierz pozycję MANAGE (ZARZĄDZAJ).":::

1. Na stronie Manage Advanced DNS Records (Zarządzanie zaawansowanymi rekordami DNS) wybierz pozycję **+ ADD RECORD (DODAJ REKORD**).

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Wybierz pozycję + ADD RECORD (DODAJ REKORD).":::

1. W **obszarze Typ** z **listy** rozwijanej wybierz pozycję TXT.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-TXT.png" alt-text="Z listy rozwijanej Type (Typ) wybierz wartość TXT.":::

1. Zaznacz lub skopiuj i wklej wartości z poniższej tabeli.

    |Refers|Wartość TXT|Czas wygaśnięcia|
    |---|---|:----|
    |@|MS=*msXXXXXXXX* <br/> **Uwaga:** To jest przykład. Użyj tutaj swojej **konkretnej** wartości Miejsce docelowe lub punkt na adres z tabeli. [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)|1 godzina|

1. Wybierz **pozycję DODAJ**.

    Przed zweryfikowaniem nowego rekordu TXT poczekaj kilka minut na zaktualizowanie utworzonego właśnie rekordu w Internecie.

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

1. Aby rozpocząć pracę, przejdź do swojej strony domen w web.com, używając [tego linku](https://checkout.web.com/manage-it/index.jsp). Zaloguj się najpierw.

1. Na stronie docelowej wybierz pozycję **Domain Names (Nazwy domen**).

1. W **obszarze** Akcje wybierz trzy kropki, a następnie z  listy rozwijanej wybierz pozycję Zarządzaj.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Z listy rozwijanej wybierz pozycję Zarządzaj.":::

1. Przewiń w dół, aby **wybrać pozycję Narzędzia zaawansowane**, a następnie obok **przycisku Advanced DNS Records (Zaawansowane rekordy DNS**) wybierz pozycję **MANAGE (ZARZĄDZAJ**).

    Może być konieczne wybranie **przycisku Continue (Kontynuuj** ), aby uzyskać dostęp do strony Manage Advanced DNS Records (Zarządzanie zaawansowanymi rekordami DNS).

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Obok przycisku Advanced DNS records (Zaawansowane rekordy DNS) wybierz pozycję MANAGE (ZARZĄDZAJ).":::

1. Na stronie Manage Advanced DNS Records (Zarządzanie zaawansowanymi rekordami DNS) wybierz pozycję **+ ADD RECORD (DODAJ REKORD**).

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Wybierz pozycję + ADD RECORD (DODAJ REKORD).":::

1. W **obszarze Typ** z **listy** rozwijanej wybierz pozycję MX.

1. Zaznacz lub skopiuj i wklej wartości z poniższej tabeli.

    |Odwołuje się do|Serwer poczty|Priority (Priorytet)|TTL (Czas wygaśnięcia)|
    |---|---|---|---|
    |@|*\<domain-key\>* mail.protection.outlook.com <br/> **Uwaga:** Pobierz swoje *\<domain-key\>* konto z centrum administracyjnego firmy Microsoft. [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)|Aby uzyskać więcej informacji o priorytetach, zobacz [Co to jest priorytet rekordu MX?](../setup/domains-faq.yml) <br/> 1|1 godzina|

1. Wybierz **pozycję DODAJ**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-mx-add.png" alt-text="Wybierz pozycję DODAJ.":::

1. Jeśli istnieją inne rekordy MX, usuń je wszystkie, wybierając narzędzie do edycji, a następnie pozycję **Delete (Usuń** ) dla każdego rekordu.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-edit.png" alt-text="Wybierz pozycję Edytuj.":::

## <a name="add-the-cname-record-required-for-microsoft"></a>Dodawanie rekordu CNAME wymaganego dla firmy Microsoft

1. Aby rozpocząć pracę, przejdź do swojej strony domen w web.com, używając [tego linku](https://checkout.web.com/manage-it/index.jsp). Zaloguj się najpierw.

1. Na stronie docelowej wybierz pozycję **Domain Names (Nazwy domen**).

1. W **obszarze** Akcje wybierz trzy kropki, a następnie z  listy rozwijanej wybierz pozycję Zarządzaj.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Z listy rozwijanej wybierz pozycję Zarządzaj.":::

1. Przewiń w dół, aby **wybrać pozycję Narzędzia zaawansowane**, a następnie obok **przycisku Advanced DNS Records (Zaawansowane rekordy DNS**) wybierz pozycję **MANAGE (ZARZĄDZAJ**).

    Może być konieczne wybranie **przycisku Continue (Kontynuuj** ), aby uzyskać dostęp do strony Manage Advanced DNS Records (Zarządzanie zaawansowanymi rekordami DNS).

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Obok przycisku Advanced DNS records (Zaawansowane rekordy DNS) wybierz pozycję MANAGE (ZARZĄDZAJ).":::

1. Na stronie Manage Advanced DNS Records (Zarządzanie zaawansowanymi rekordami DNS) wybierz pozycję **+ ADD RECORD (DODAJ REKORD**).

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Wybierz pozycję + ADD RECORD (DODAJ REKORD).":::

1. W **obszarze Typ** wybierz **pozycję CNAME** z listy rozwijanej.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="Z listy rozwijanej Type (Typ) wybierz pozycję CNAME.":::

1. Zaznacz lub skopiuj i wklej wartości z poniższej tabeli.

    |Odwołuje się do|Nazwa hosta|Alias to (Alias)|Czas wygaśnięcia|
    |---|---|---|---|
    |Inny host|autodiscover|autodiscover.outlook.com|1 godzina|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="Wpisz lub skopiuj i wklej wartości CNAME w oknie.":::

1. Wybierz **pozycję DODAJ**.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Dodawanie rekordu TXT SPF w celu zapobiegania spamowi w wiadomościach e-mail

> [!IMPORTANT]
> Nie można mieć więcej niż jednego rekordu TXT na rekord SPF dla domeny. Jeśli domena ma więcej niż jeden rekord SPF, może to spowodować błędy poczty e-mail, a także problemy z dostarczaniem i klasyfikacją spamu. Jeśli masz już rekord SPF dla swojej domeny, nie twórz nowego rekordu dla firmy Microsoft. Zamiast tego dodaj wymagane wartości firmy Microsoft do bieżącego rekordu, aby mieć pojedynczy *rekord SPF,* który zawiera oba zestawy wartości.

1. Aby rozpocząć pracę, przejdź do swojej strony domen w web.com, używając [tego linku](https://checkout.web.com/manage-it/index.jsp). Zaloguj się najpierw.

1. Na stronie docelowej wybierz pozycję **Domain Names (Nazwy domen**).

1. W **obszarze** Akcje wybierz trzy kropki, a następnie z  listy rozwijanej wybierz pozycję Zarządzaj.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Z listy rozwijanej wybierz pozycję Zarządzaj.":::

1. Przewiń w dół, aby **wybrać pozycję Narzędzia zaawansowane**, a następnie obok **przycisku Advanced DNS Records (Zaawansowane rekordy DNS**) wybierz pozycję **MANAGE (ZARZĄDZAJ**).

    Może być konieczne wybranie **przycisku Continue (Kontynuuj** ), aby uzyskać dostęp do strony Manage Advanced DNS Records (Zarządzanie zaawansowanymi rekordami DNS).

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Obok przycisku Advanced DNS records (Zaawansowane rekordy DNS) wybierz pozycję MANAGE (ZARZĄDZAJ).":::

1. Na stronie Manage Advanced DNS Records (Zarządzanie zaawansowanymi rekordami DNS) wybierz pozycję **+ ADD RECORD (DODAJ REKORD**).

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Wybierz pozycję + ADD RECORD (DODAJ REKORD).":::

1. W **obszarze Typ** z **listy** rozwijanej wybierz pozycję TXT.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-TXT.png" alt-text="Z listy rozwijanej Type (Typ) wybierz wartość TXT.":::

1. Zaznacz lub skopiuj i wklej wartości z poniższej tabeli.

    |Odwołuje się do|Wartość TXT|Czas wygaśnięcia|
    |---|---|---|
    |@|v=spf1 include:spf.protection.outlook.com -all <br/> **Uwaga:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostawały poprawne.|1 godzina|

1. Wybierz **pozycję DODAJ**.

## <a name="advanced-option-skype-for-business"></a>Opcja Zaawansowane: Skype dla firm

Wybierz tę opcję tylko wtedy, gdy Twoja organizacja korzysta Skype dla firm usług komunikacji online, takich jak czat, połączenia konferencyjne i połączenia wideo, oprócz Microsoft Teams. Skype 4 rekordy: 2 rekordy SRV do komunikacji między użytkownikami i 2 rekordy CNAME do zalogowania się i połączenia użytkowników z usługą.

### <a name="add-the-two-required-srv-records"></a>Dodawanie dwóch wymaganych rekordów SRV

1. Aby rozpocząć pracę, przejdź do swojej strony domen w web.com, używając [tego linku](https://checkout.web.com/manage-it/index.jsp). Zaloguj się najpierw.

1. Na stronie docelowej wybierz pozycję **Domain Names (Nazwy domen**).

1. W **obszarze** Akcje wybierz trzy kropki, a następnie z  listy rozwijanej wybierz pozycję Zarządzaj.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Z listy rozwijanej wybierz pozycję Zarządzaj.":::

1. Przewiń w dół, aby **wybrać pozycję Narzędzia zaawansowane**, a następnie obok **przycisku Advanced DNS Records (Zaawansowane rekordy DNS**) wybierz pozycję **MANAGE (ZARZĄDZAJ**).

    Może być konieczne wybranie **przycisku Continue (Kontynuuj** ), aby uzyskać dostęp do strony Manage Advanced DNS Records (Zarządzanie zaawansowanymi rekordami DNS).

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Obok przycisku Advanced DNS records (Zaawansowane rekordy DNS) wybierz pozycję MANAGE (ZARZĄDZAJ).":::

1. Na stronie Manage Advanced DNS Records (Zarządzanie zaawansowanymi rekordami DNS) wybierz pozycję **+ ADD RECORD (DODAJ REKORD**).

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Wybierz pozycję + ADD RECORD (DODAJ REKORD).":::

1. W **obszarze Typ** z **listy rozwijanej wybierz pozycję SRV** .

    :::image type="content" source="../../media/dns-webcom/webcom-domains-srv.png" alt-text="Z listy rozwijanej Type (Typ) wybierz pozycję SRV.":::

1. Zaznacz lub skopiuj i wklej wartości z poniższej tabeli.

    |Wpisać|Usługa|Protocol (Protokół)|Waga|Port|Target (Element docelowy)|Priority (Priorytet)|TTL (Czas wygaśnięcia)|
    |---|---|---|---|---|---|---|---|
    |SRV|_sip|TLS|100|443|sipdir.online.lync.com <br/> **Ta wartość NIE MOŻE kończyć się okresem (.)**|1|1 godzina|
    |SRV|_sipfederationtls|TCP|100|5061|sipfed.online.lync.com <br/> **Ta wartość NIE MOŻE kończyć się okresem (.)**|1|1 godzina|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-srv-add.png" alt-text="Wpisz lub skopiuj i wklej wartości z tabeli w oknie rekordu SRV.":::

1. Wybierz **pozycję DODAJ**.

1. Dodaj drugi rekord SRV, kopiując wartości z drugiego wiersza tabeli.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS masz problemy z przepływem poczty e-mail lub inne, zobacz Znajdowanie i rozwiązywanie problemów po dodaniu domeny lub [rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records"></a>Dodawanie dwóch wymaganych rekordów CNAME

1. Aby rozpocząć pracę, przejdź do swojej strony domen w web.com, używając [tego linku](https://checkout.web.com/manage-it/index.jsp). Zaloguj się najpierw.

1. Na stronie docelowej wybierz pozycję **Domain Names (Nazwy domen**).

1. W **obszarze** Akcje wybierz trzy kropki, a następnie z  listy rozwijanej wybierz pozycję Zarządzaj.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Z listy rozwijanej wybierz pozycję Zarządzaj.":::

1. Przewiń w dół, aby **wybrać pozycję Narzędzia zaawansowane**, a następnie obok **przycisku Advanced DNS Records (Zaawansowane rekordy DNS**) wybierz pozycję **MANAGE (ZARZĄDZAJ**).

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Obok przycisku Advanced DNS records (Zaawansowane rekordy DNS) wybierz pozycję MANAGE (ZARZĄDZAJ).":::

    Może być konieczne wybranie **przycisku Continue (Kontynuuj** ), aby uzyskać dostęp do strony Manage Advanced DNS Records (Zarządzanie zaawansowanymi rekordami DNS).

1. Na stronie Manage Advanced DNS Records (Zarządzanie zaawansowanymi rekordami DNS) wybierz pozycję **+ ADD RECORD (DODAJ REKORD**).

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Wybierz pozycję + ADD RECORD (DODAJ REKORD).":::

1. W **obszarze Typ** wybierz **pozycję CNAME** z listy rozwijanej.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="Z listy rozwijanej Type (Typ) wybierz pozycję CNAME.":::

1. Zaznacz lub skopiuj i wklej wartości z poniższej tabeli.

    |Wpisać|Odwołuje się do|Host Name|Alias to (Alias)|Czas wygaśnięcia|
    |---|---|---|---|---|
    |CNAME|Inny host|sip|sipdir.online.lync.com <br/> **Ta wartość NIE MOŻE kończyć się okresem (.)**|1 godzina|
    |CNAME|Inny host|lyncdiscover|webdir.online.lync.com <br/> **Ta wartość NIE MOŻE kończyć się okresem (.)**|1 godzina|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="Wpisz lub skopiuj i wklej wartości CNAME w oknie.":::

1. Wybierz **pozycję DODAJ**.

1. Dodaj drugi rekord CNAME, kopiując wartości z drugiego wiersza tabeli.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Opcja Zaawansowane: opcje Intune i Mobile Zarządzanie urządzeniami dla Microsoft 365

Ta usługa ułatwia zabezpieczanie urządzeń przenośnych, które nawiązą połączenie z domeną, i zdalne zarządzanie nimi. Usługa Zarządzanie urządzeniami wymaga 2 rekordów CNAME, aby użytkownicy mogą rejestrować urządzenia do usługi.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Dodaj dwa wymagane rekordy CNAME dla usługi Mobile Zarządzanie urządzeniami

1. Aby rozpocząć pracę, przejdź do swojej strony domen w web.com, używając [tego linku](https://checkout.web.com/manage-it/index.jsp). Zaloguj się najpierw.

1. Na stronie docelowej wybierz pozycję **Domain Names (Nazwy domen**).

1. W **obszarze** Akcje wybierz trzy kropki, a następnie z  listy rozwijanej wybierz pozycję Zarządzaj.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Z listy rozwijanej wybierz pozycję Zarządzaj.":::

1. Przewiń w dół, aby **wybrać pozycję Narzędzia zaawansowane**, a następnie obok **przycisku Advanced DNS Records (Zaawansowane rekordy DNS**) wybierz pozycję **MANAGE (ZARZĄDZAJ**).

    Może być konieczne wybranie **przycisku Continue (Kontynuuj** ), aby uzyskać dostęp do strony Manage Advanced DNS Records (Zarządzanie zaawansowanymi rekordami DNS).

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Obok przycisku Advanced DNS records (Zaawansowane rekordy DNS) wybierz pozycję MANAGE (ZARZĄDZAJ).":::

1. Na stronie Manage Advanced DNS Records (Zarządzanie zaawansowanymi rekordami DNS) wybierz pozycję **+ ADD RECORD (DODAJ REKORD**).

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Wybierz pozycję + ADD RECORD (DODAJ REKORD).":::

1. W **obszarze Typ** wybierz **pozycję CNAME** z listy rozwijanej.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="Z listy rozwijanej Type (Typ) wybierz pozycję CNAME.":::

1. Zaznacz lub skopiuj i wklej wartości z poniższej tabeli.

    |Wpisać|Odwołuje się do|Host Name|Alias to (Alias)|Czas wygaśnięcia|
    |---|---|---|---|---|
    |CNAME|Inny host|enterpriseregistration|enterpriseregistration.windows.net <br/> **Ta wartość NIE MOŻE kończyć się okresem (.)**|1 godzina|
    |CNAME|Inny host|enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com <br/> **Ta wartość NIE MOŻE kończyć się okresem (.)**|1 godzina|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="Wpisz lub skopiuj i wklej wartości CNAME z tabeli w oknie.":::

1. Wybierz **pozycję DODAJ**.

1. Dodaj drugi rekord CNAME, kopiując wartości z drugiego wiersza tabeli.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).
