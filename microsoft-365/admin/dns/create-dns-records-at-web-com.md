---
title: Łączenie rekordów DNS w web.com z platformą Microsoft 365
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
ms.assetid: 84acd4fc-6eec-4d00-8bed-568f036ae2af
description: Dowiedz się, jak zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, Skype dla firm Online i innych usług w web.com dla firmy Microsoft.
ms.openlocfilehash: d247ee24c107318289dfbca0ee741d5a04725d25
ms.sourcegitcommit: 8cd230e243eba452b27f725d66152becb6aff49b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2022
ms.locfileid: "66563236"
---
# <a name="connect-your-dns-records-at-webcom-to-microsoft-365"></a>Łączenie rekordów DNS w web.com z platformą Microsoft 365

 **[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji.

Jeśli web.com jest dostawcą hostingu DNS, wykonaj kroki opisane w tym artykule, aby zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, Skype dla firm Online itd.

Po dodaniu tych rekordów w web.com domena zostanie skonfigurowana do pracy z usługami firmy Microsoft.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="change-your-domains-nameserver-ns-records"></a>Zmienianie rekordów serwerów nazw domeny (SN)

> [!IMPORTANT]
> Tę procedurę należy wykonać w witrynie rejestratora domen, u którego kupiono i zarejestrowano domenę.

Po zarejestrowaniu się w celu web.com dodano domenę przy użyciu procesu **konfiguracji** web.com.

Aby zweryfikować i utworzyć rekordy DNS dla domeny w firmie Microsoft, należy najpierw zmienić serwery nazw u rejestratora domen, tak aby używały web.com serwerów nazw.

Aby samodzielnie zmienić serwery nazw domen w witrynie sieci Web rejestratora domen, wykonaj poniższe czynności.

1. Znajdź obszar w witrynie sieci Web rejestratora domen, w którym można edytować serwery nazw dla Twojej domeny.

2. Utwórz dwa rekordy programu nameserver przy użyciu wartości w poniższej tabeli lub edytuj istniejące rekordy serwera nazw, aby były zgodne z tymi wartościami.

    |Wpisać|Value|
    |---|---|
    |Pierwszy serwer nazw|Użyj wartości elementu nazw dostarczonej przez web.com.|
    |Drugi serwer nazw|Użyj wartości elementu nazw dostarczonej przez web.com.|

    > [!TIP]
    > Należy użyć co najmniej dwóch rekordów serwera nazw. Jeśli na liście znajdują się inne serwery nazw, należy je usunąć.

3. Zapisz zmiany.

> [!NOTE]
> Aktualizowanie rekordu serwera nazw w internetowym systemie DNS może potrwać nawet kilka godzin. Następnie poczta e-mail firmy Microsoft i inne usługi zostaną ustawione do pracy z Domeną.

## <a name="add-a-txt-record-for-verification"></a>Dodawanie rekordu TXT w celu weryfikacji

Przed użyciem domeny z firmą Microsoft musimy upewnić się, że jesteś jej właścicielem. Możliwość zalogowania się do konta u rejestratora domen i utworzenia rekordu DNS potwierdza firmie Microsoft, że jesteś właścicielem domeny.

> [!NOTE]
> Ten rekord jest używany tylko do weryfikowania, że jesteś właścicielem domeny, i nie wywiera wpływu na nic innego. Jeśli chcesz, możesz go później usunąć.

1. Aby rozpocząć, przejdź do strony domen pod adresem web.com, korzystając z [tego linku](https://checkout.web.com/manage-it/index.jsp). Zaloguj się jako pierwszy.

1. Na stronie docelowej wybierz pozycję **Nazwy domen**.

1. W obszarze **Akcje** wybierz trzy kropki, a następnie wybierz pozycję **Zarządzaj** z listy rozwijanej.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Wybierz pozycję Zarządzaj z listy rozwijanej.":::

1. Przewiń w dół, aby wybrać pozycję **Narzędzia zaawansowane**, a następnie obok pozycji **Zaawansowane rekordy DNS** wybierz pozycję **ZARZĄDZAJ**.

    Może być konieczne wybranie pozycji **Kontynuuj** , aby przejść do strony Zarządzanie zaawansowanymi rekordami DNS.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Obok pozycji Zaawansowane rekordy DNS wybierz pozycję ZARZĄDZAJ.":::

1. Na stronie Zarządzanie zaawansowanymi rekordami DNS wybierz pozycję **+ DODAJ REKORD**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Wybierz pozycję + DODAJ REKORD.":::

1. W obszarze **Typ** wybierz pozycję **TXT** z listy rozwijanej.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-TXT.png" alt-text="Wybierz pozycję TXT z listy rozwijanej Typ.":::

1. Wybierz lub skopiuj i wklej wartości z poniższej tabeli.

    |Odnosi się|Wartość TXT|Czas wygaśnięcia|
    |---|---|:----|
    |@|MS=ms *XXXXXXXXXX* <br/> **Uwaga:** Jest to przykład. W tym miejscu użyj określonej wartości **Destination (Miejsce docelowe) lub Points to Address (Punkty do adresu** ) z tabeli . [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)|1 godzina|

1. Wybierz pozycję **DODAJ**.

    Poczekaj kilka minut, zanim zweryfikujesz nowy rekord TXT, aby właśnie utworzony rekord mógł być aktualizowany przez Internet.

Po dodaniu rekordu w witrynie rejestratora domen wrócisz do firmy Microsoft i zażądasz rekordu. Gdy firma Microsoft znajdzie właściwy rekord TXT, domena zostanie zweryfikowana.

Aby zweryfikować rekord w usłudze Microsoft 365:

1. W centrum administracyjnym przejdź do obszaru **Domeny ustawień**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank"></a>

1. Na stronie Domeny wybierz domenę, którą weryfikujesz, a następnie wybierz pozycję **Rozpocznij konfigurację**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Wybierz pozycję Rozpocznij konfigurację.":::

1. Naciśnij przycisk **Kontynuuj**.

1. Na stronie **Weryfikowanie domeny** wybierz pozycję **Weryfikuj**.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Dodaj rekord MX, aby wiadomość e-mail dla twojej domeny przyszła do firmy Microsoft

1. Aby rozpocząć, przejdź do strony domen pod adresem web.com, korzystając z [tego linku](https://checkout.web.com/manage-it/index.jsp). Zaloguj się jako pierwszy.

1. Na stronie docelowej wybierz pozycję **Nazwy domen**.

1. W obszarze **Akcje** wybierz trzy kropki, a następnie wybierz pozycję **Zarządzaj** z listy rozwijanej.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Wybierz pozycję Zarządzaj z listy rozwijanej.":::

1. Przewiń w dół, aby wybrać pozycję **Narzędzia zaawansowane**, a następnie obok pozycji **Zaawansowane rekordy DNS** wybierz pozycję **ZARZĄDZAJ**.

    Może być konieczne wybranie pozycji **Kontynuuj** , aby przejść do strony Zarządzanie zaawansowanymi rekordami DNS.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Obok pozycji Zaawansowane rekordy DNS wybierz pozycję ZARZĄDZAJ.":::

1. Na stronie Zarządzanie zaawansowanymi rekordami DNS wybierz pozycję **+ DODAJ REKORD**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Wybierz pozycję + DODAJ REKORD.":::

1. W obszarze **Typ** wybierz pozycję **MX** z listy rozwijanej.

1. Wybierz lub skopiuj i wklej wartości z poniższej tabeli.

    |Odwołuje się do|Serwer poczty|Priority (Priorytet)|TTL (Czas wygaśnięcia)|
    |---|---|---|---|
    |@|*\<domain-key\>*.mail.protection.outlook.com <br/> **Uwaga:** Pobierz dane *\<domain-key\>* z centrum administracyjnego firmy Microsoft. [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)|Aby uzyskać więcej informacji o priorytetach, zobacz [Co to jest priorytet rekordu MX?](../setup/domains-faq.yml) <br/> 1|1 godzina|

1. Wybierz pozycję **DODAJ**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-mx-add.png" alt-text="Wybierz pozycję DODAJ.":::

1. Jeśli istnieją inne rekordy MX, usuń wszystkie z nich, wybierając narzędzie do edycji, a następnie **usuń** dla każdego rekordu.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-edit.png" alt-text="Wybierz pozycję Edytuj.":::

## <a name="add-the-cname-record-required-for-microsoft"></a>Dodawanie rekordu CNAME wymaganego dla firmy Microsoft

1. Aby rozpocząć, przejdź do strony domen pod adresem web.com, korzystając z [tego linku](https://checkout.web.com/manage-it/index.jsp). Zaloguj się jako pierwszy.

1. Na stronie docelowej wybierz pozycję **Nazwy domen**.

1. W obszarze **Akcje** wybierz trzy kropki, a następnie wybierz pozycję **Zarządzaj** z listy rozwijanej.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Wybierz pozycję Zarządzaj z listy rozwijanej.":::

1. Przewiń w dół, aby wybrać pozycję **Narzędzia zaawansowane**, a następnie obok pozycji **Zaawansowane rekordy DNS** wybierz pozycję **ZARZĄDZAJ**.

    Może być konieczne wybranie pozycji **Kontynuuj** , aby przejść do strony Zarządzanie zaawansowanymi rekordami DNS.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Obok pozycji Zaawansowane rekordy DNS wybierz pozycję ZARZĄDZAJ.":::

1. Na stronie Zarządzanie zaawansowanymi rekordami DNS wybierz pozycję **+ DODAJ REKORD**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Wybierz pozycję + DODAJ REKORD.":::

1. W obszarze **Typ** wybierz pozycję **CNAME** z listy rozwijanej.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="Wybierz pozycję CNAME z listy rozwijanej Typ.":::

1. Wybierz lub skopiuj i wklej wartości z poniższej tabeli.

    |Odwołuje się do|Nazwa hosta|Alias to (Alias)|Czas wygaśnięcia|
    |---|---|---|---|
    |Inny host|autodiscover|autodiscover.outlook.com|1 godzina|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="Wpisz lub skopiuj i wklej wartości CNAME w oknie.":::

1. Wybierz pozycję **DODAJ**.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Dodawanie rekordu TXT SPF w celu zapobiegania spamowi w wiadomościach e-mail

> [!IMPORTANT]
> Nie można mieć więcej niż jednego rekordu TXT na rekord SPF dla domeny. Jeśli domena ma więcej niż jeden rekord SPF, może to spowodować błędy poczty e-mail, a także problemy z dostarczaniem i klasyfikacją spamu. Jeśli masz już rekord SPF dla swojej domeny, nie twórz nowego rekordu dla firmy Microsoft. Zamiast tego dodaj wymagane wartości firmy Microsoft do bieżącego rekordu, aby mieć *jeden* rekord SPF zawierający oba zestawy wartości.

1. Aby rozpocząć, przejdź do strony domen pod adresem web.com, korzystając z [tego linku](https://checkout.web.com/manage-it/index.jsp). Zaloguj się jako pierwszy.

1. Na stronie docelowej wybierz pozycję **Nazwy domen**.

1. W obszarze **Akcje** wybierz trzy kropki, a następnie wybierz pozycję **Zarządzaj** z listy rozwijanej.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Wybierz pozycję Zarządzaj z listy rozwijanej.":::

1. Przewiń w dół, aby wybrać pozycję **Narzędzia zaawansowane**, a następnie obok pozycji **Zaawansowane rekordy DNS** wybierz pozycję **ZARZĄDZAJ**.

    Może być konieczne wybranie pozycji **Kontynuuj** , aby przejść do strony Zarządzanie zaawansowanymi rekordami DNS.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Obok pozycji Zaawansowane rekordy DNS wybierz pozycję ZARZĄDZAJ.":::

1. Na stronie Zarządzanie zaawansowanymi rekordami DNS wybierz pozycję **+ DODAJ REKORD**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Wybierz pozycję + DODAJ REKORD.":::

1. W obszarze **Typ** wybierz pozycję **TXT** z listy rozwijanej.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-TXT.png" alt-text="Wybierz pozycję TXT z listy rozwijanej Typ.":::

1. Wybierz lub skopiuj i wklej wartości z poniższej tabeli.

    |Odwołuje się do|Wartość TXT|Czas wygaśnięcia|
    |---|---|---|
    |@|v=spf1 include:spf.protection.outlook.com -all <br/> **Uwaga:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostały poprawne.|1 godzina|

1. Wybierz pozycję **DODAJ**.

## <a name="advanced-option-skype-for-business"></a>Opcja zaawansowana: Skype dla firm

Tę opcję należy wybrać tylko wtedy, gdy organizacja używa Skype dla firm dla usług komunikacji online, takich jak czat, połączenia konferencyjne i połączenia wideo, oprócz usługi Microsoft Teams. Skype potrzebuje 4 rekordów: 2 rekordy SRV do komunikacji między użytkownikami i 2 rekordy CNAME, aby zalogować się i połączyć użytkowników z usługą.

### <a name="add-the-two-required-srv-records"></a>Dodawanie dwóch wymaganych rekordów SRV

1. Aby rozpocząć, przejdź do strony domen pod adresem web.com, korzystając z [tego linku](https://checkout.web.com/manage-it/index.jsp). Zaloguj się jako pierwszy.

1. Na stronie docelowej wybierz pozycję **Nazwy domen**.

1. W obszarze **Akcje** wybierz trzy kropki, a następnie wybierz pozycję **Zarządzaj** z listy rozwijanej.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Wybierz pozycję Zarządzaj z listy rozwijanej.":::

1. Przewiń w dół, aby wybrać pozycję **Narzędzia zaawansowane**, a następnie obok pozycji **Zaawansowane rekordy DNS** wybierz pozycję **ZARZĄDZAJ**.

    Może być konieczne wybranie pozycji **Kontynuuj** , aby przejść do strony Zarządzanie zaawansowanymi rekordami DNS.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Obok pozycji Zaawansowane rekordy DNS wybierz pozycję ZARZĄDZAJ.":::

1. Na stronie Zarządzanie zaawansowanymi rekordami DNS wybierz pozycję **+ DODAJ REKORD**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Wybierz pozycję + DODAJ REKORD.":::

1. W obszarze **Typ** wybierz pozycję **SRV** z listy rozwijanej.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-srv.png" alt-text="Wybierz pozycję SRV z listy rozwijanej Typ.":::

1. Wybierz lub skopiuj i wklej wartości z poniższej tabeli.

    |Wpisać|Usługa|Protocol (Protokół)|Waga|Port|Target (Element docelowy)|Priority (Priorytet)|TTL (Czas wygaśnięcia)|
    |---|---|---|---|---|---|---|---|
    |SRV|_sip|TLS|100|443|sipdir.online.lync.com <br/> **Ta wartość nie może kończyć się kropką (.)**|1|1 godzina|
    |SRV|_sipfederationtls|TCP|100|5061|sipfed.online.lync.com <br/> **Ta wartość nie może kończyć się kropką (.)**|1|1 godzina|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-srv-add.png" alt-text="Wpisz lub skopiuj i wklej wartości z tabeli do okna rekordu SRV.":::

1. Wybierz pozycję **DODAJ**.

1. Dodaj inny rekord SRV, kopiując wartości z drugiego wiersza tabeli.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli masz problemy z przepływem poczty lub inne problemy po dodaniu rekordów DNS, zobacz [Znajdowanie i rozwiązywanie problemów po dodaniu domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Dodaj dwa wymagane rekordy CNAME dla Skype dla firm

1. Aby rozpocząć, przejdź do strony domen pod adresem web.com, korzystając z [tego linku](https://checkout.web.com/manage-it/index.jsp). Zaloguj się jako pierwszy.

1. Na stronie docelowej wybierz pozycję **Nazwy domen**.

1. W obszarze **Akcje** wybierz trzy kropki, a następnie wybierz pozycję **Zarządzaj** z listy rozwijanej.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Wybierz pozycję Zarządzaj z listy rozwijanej.":::

1. Przewiń w dół, aby wybrać pozycję **Narzędzia zaawansowane**, a następnie obok pozycji **Zaawansowane rekordy DNS** wybierz pozycję **ZARZĄDZAJ**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Obok pozycji Zaawansowane rekordy DNS wybierz pozycję ZARZĄDZAJ.":::

    Może być konieczne wybranie pozycji **Kontynuuj** , aby przejść do strony Zarządzanie zaawansowanymi rekordami DNS.

1. Na stronie Zarządzanie zaawansowanymi rekordami DNS wybierz pozycję **+ DODAJ REKORD**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Wybierz pozycję + DODAJ REKORD.":::

1. W obszarze **Typ** wybierz pozycję **CNAME** z listy rozwijanej.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="Wybierz pozycję CNAME z listy rozwijanej Typ.":::

1. Wybierz lub skopiuj i wklej wartości z poniższej tabeli.

    |Wpisać|Odwołuje się do|Nazwa hosta|Alias to (Alias)|Czas wygaśnięcia|
    |---|---|---|---|---|
    |CNAME|Inny host|sip|sipdir.online.lync.com <br/> **Ta wartość nie może kończyć się kropką (.)**|1 godzina|
    |CNAME|Inny host|lyncdiscover|webdir.online.lync.com <br/> **Ta wartość nie może kończyć się kropką (.)**|1 godzina|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="Wpisz lub skopiuj i wklej wartości CNAME w oknie.":::

1. Wybierz pozycję **DODAJ**.

1. Dodaj inny rekord CNAME, kopiując wartości z drugiego wiersza tabeli.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Opcja zaawansowana: Intune i mobile Zarządzanie urządzeniami dla platformy Microsoft 365

Ta usługa ułatwia zabezpieczanie i zdalne zarządzanie urządzeniami przenośnymi łączącymi się z domeną. Usługa Mobile Zarządzanie urządzeniami wymaga 2 rekordów CNAME, aby użytkownicy mogli rejestrować urządzenia w usłudze.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Dodaj dwa wymagane rekordy CNAME dla usługi Mobile Zarządzanie urządzeniami

1. Aby rozpocząć, przejdź do strony domen pod adresem web.com, korzystając z [tego linku](https://checkout.web.com/manage-it/index.jsp). Zaloguj się jako pierwszy.

1. Na stronie docelowej wybierz pozycję **Nazwy domen**.

1. W obszarze **Akcje** wybierz trzy kropki, a następnie wybierz pozycję **Zarządzaj** z listy rozwijanej.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Wybierz pozycję Zarządzaj z listy rozwijanej.":::

1. Przewiń w dół, aby wybrać pozycję **Narzędzia zaawansowane**, a następnie obok pozycji **Zaawansowane rekordy DNS** wybierz pozycję **ZARZĄDZAJ**.

    Może być konieczne wybranie pozycji **Kontynuuj** , aby przejść do strony Zarządzanie zaawansowanymi rekordami DNS.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Obok pozycji Zaawansowane rekordy DNS wybierz pozycję ZARZĄDZAJ.":::

1. Na stronie Zarządzanie zaawansowanymi rekordami DNS wybierz pozycję **+ DODAJ REKORD**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Wybierz pozycję + DODAJ REKORD.":::

1. W obszarze **Typ** wybierz pozycję **CNAME** z listy rozwijanej.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="Wybierz pozycję CNAME z listy rozwijanej Typ.":::

1. Wybierz lub skopiuj i wklej wartości z poniższej tabeli.

    |Wpisać|Odwołuje się do|Nazwa hosta|Alias to (Alias)|Czas wygaśnięcia|
    |---|---|---|---|---|
    |CNAME|Inny host|enterpriseregistration|enterpriseregistration.windows.net <br/> **Ta wartość nie może kończyć się kropką (.)**|1 godzina|
    |CNAME|Inny host|enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com <br/> **Ta wartość nie może kończyć się kropką (.)**|1 godzina|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="Wpisz lub skopiuj i wklej wartości CNAME z tabeli do okna.":::

1. Wybierz pozycję **DODAJ**.

1. Dodaj inny rekord CNAME, kopiując wartości z drugiego wiersza tabeli.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).
