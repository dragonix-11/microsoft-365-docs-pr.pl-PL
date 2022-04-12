---
title: Połączenie rekordy DNS w systemie IONOS o 1&1 do Microsoft 365
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
ms.assetid: 5762c3ca-1de2-4999-bfe5-4c5e25a8957e
description: Dowiedz się, jak zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, Skype dla firm Online i innych usług pod adresem 1&1 IONOS dla firmy Microsoft.
ms.openlocfilehash: 8afdfed0998a262b1df4c95a63e9086e4f71e5b6
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780682"
---
# <a name="connect-your-dns-records-at-ionos-by-11-to-microsoft-365"></a>Połączenie rekordy DNS w systemie IONOS o 1&1 do Microsoft 365

 **[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji.

Jeśli usługa IONOS by 1&1 jest dostawcą hostingu DNS, wykonaj kroki opisane w tym artykule, aby zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, Skype dla firm Online itd.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Istnieją dwie opcje konfigurowania rekordów DNS dla domeny:

- [**Użyj Połączenie domeny**](#use-domain-connect-to-verify-and-set-up-your-domain) Jeśli nie skonfigurowano domeny z innym dostawcą usług poczty e-mail, wykonaj kroki Połączenie domeny, aby automatycznie zweryfikować i skonfigurować nową domenę do użycia z Microsoft 365.

    LUB

- [**Wykonaj kroki ręczne**](#create-dns-records-with-manual-setup) Zweryfikuj domenę, wykonując poniższe kroki ręcznie, i wybierz, kiedy i które rekordy należy dodać do rejestratora domeny. Dzięki temu można skonfigurować nowe rekordy MX (poczty e-mail), na przykład dla Twojej wygody.

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>Weryfikowanie i konfigurowanie domeny przy użyciu Połączenie domeny

Wykonaj następujące kroki, aby automatycznie zweryfikować i skonfigurować domenę IONOS by 1&1 przy użyciu Microsoft 365:

1. W Centrum administracyjne platformy Microsoft 365 wybierz pozycję **Ustawienia** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domeny**</a> i wybierz domenę, którą chcesz skonfigurować.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-1.png" alt-text="Wybierz domenę w Microsoft 365.":::

1. Wybierz trzy kropki (więcej akcji), > wybierz pozycję **Rozpocznij instalację**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Wybierz pozycję Rozpocznij konfigurację.":::

1. Na stronie Jak chcesz połączyć domenę? wybierz pozycję **Kontynuuj**.

1. Na stronie Dodawanie rekordów DNS wybierz pozycję **Dodaj rekordy DNS**.

1. Na stronie logowania IONOS by 1&1 zaloguj się do swojego konta, a następnie wybierz pozycję **Połączenie** i **Zezwalaj**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-3.png" alt-text="Wybierz pozycję Połączenie, a następnie pozycję Zezwalaj.":::

    Spowoduje to ukończenie konfiguracji domeny dla Microsoft 365.

## <a name="create-dns-records-with-manual-setup"></a>Tworzenie rekordów DNS z ręczną konfiguracją

Po dodaniu tych rekordów w usłudze IONOS do 1&1 domena zostanie skonfigurowana do pracy z usługi firmy Microsoft.

> [!CAUTION]
> Należy pamiętać, że protokół IONOS by 1&1 nie zezwala domenie na posiadanie zarówno rekordu MX, jak i rekordu CNAME automatycznego wykrywania najwyższego poziomu. Ogranicza to sposoby konfigurowania Exchange Online dla firmy Microsoft. Istnieje obejście problemu, ale zalecamy zastosowanie go **tylko** wtedy, gdy masz już doświadczenie w tworzeniu domen podrzędnych w usłudze IONOS przez 1&1.
> Jeśli pomimo tego [ograniczenia usługi](../setup/domains-faq.yml) wybierzesz zarządzanie własnymi rekordami DNS firmy Microsoft w usłudze IONOS do 1&1, wykonaj kroki opisane w tym artykule, aby zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, Skype dla firm Online itd.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli masz problemy z przepływem poczty lub inne problemy po dodaniu rekordów DNS, zobacz [Znajdowanie i rozwiązywanie problemów po dodaniu domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-a-txt-record-for-verification"></a>Dodawanie rekordu TXT w celu weryfikacji

Przed użyciem domeny z firmą Microsoft musimy upewnić się, że jesteś jej właścicielem. Możliwość zalogowania się do konta u rejestratora domen i utworzenia rekordu DNS potwierdza firmie Microsoft, że jesteś właścicielem domeny.

> [!NOTE]
> Ten rekord jest używany tylko do weryfikowania, że jesteś właścicielem domeny, i nie wywiera wpływu na nic innego. Jeśli chcesz, możesz go później usunąć.

1. Aby rozpocząć, przejdź do strony domen w witrynie IONOS by 1&1, korzystając z [tego linku](https://my.1and1.com/). Zostanie wyświetlony monit o zalogowanie się.

1. Wybierz pozycję **Menu**, a następnie wybierz pozycję **Domeny i protokół SSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Wybierz pozycję Domeny i protokół SSL.":::

1. W obszarze **Akcje** dla domeny, którą chcesz zaktualizować, wybierz kontrolkę koła zębatego, a następnie wybierz pozycję **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Wybierz pozycję DNS z listy rozwijanej.":::

1. Wybierz pozycję **Dodaj rekord**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Wybierz pozycję Dodaj rekord.":::

1. Wybierz sekcję **TXT** .

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-4.png" alt-text="Wybierz sekcję TXT.":::

1. Na stronie Dodawanie rekordu DNS w polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli.

    |Nazwa hosta|Value|Czas wygaśnięcia|
    |---|---|---|
    |(Pozostaw to pole puste)|MS=ms *XXXXXXXX*  <br/> UWAGA: Jest to przykład. W tym miejscu użyj określonej wartości **Destination (Miejsce docelowe) lub Points to Address (Punkty do adresu** ) z tabeli . [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)|1 godzina|

1. Wybierz **Zapisz**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-5.png" alt-text="Wybierz pozycję Zapisz.":::

    Przed kontynuowaniem poczekaj kilka minut na zaktualizowanie utworzonego właśnie rekordu w Internecie.

Po dodaniu rekordu w witrynie rejestratora domen wrócisz do Microsoft 365 i zażądasz Microsoft 365 w celu wyszukania rekordu. Gdy firma Microsoft znajdzie właściwy rekord TXT, domena zostanie zweryfikowana.

Aby zweryfikować rekord w Microsoft 365:

1. W centrum administracyjnym przejdź do **obszaru domeny Ustawienia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**.**</a>

1. Na stronie Domeny wybierz domenę, którą weryfikujesz, a następnie wybierz pozycję **Rozpocznij konfigurację**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Wybierz pozycję Rozpocznij konfigurację.":::

1. Wybierz pozycję **Kontynuuj**.

1. Na stronie **Weryfikowanie domeny** wybierz pozycję **Weryfikuj**.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Dodaj rekord MX, aby wiadomość e-mail dla twojej domeny przyszła do firmy Microsoft

> [!NOTE]
> Jeśli zarejestrowano się w 1und1.de, [zaloguj się tutaj](https://go.microsoft.com/fwlink/?linkid=859152).

1. Aby rozpocząć, przejdź do strony domen w witrynie IONOS by 1&1, korzystając z [tego linku](https://my.1and1.com/). Zostanie wyświetlony monit o zalogowanie się.

1. Wybierz pozycję **Menu**, a następnie wybierz pozycję **Domeny i protokół SSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Wybierz pozycję Domeny i protokół SSL.":::

1. W obszarze **Akcje** dla domeny, którą chcesz zaktualizować, wybierz kontrolkę koła zębatego, a następnie wybierz pozycję **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Wybierz pozycję DNS z listy rozwijanej.":::

1. Wybierz pozycję **Dodaj rekord**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Wybierz pozycję Dodaj rekord.":::

1. Wybierz sekcję **MX** .

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-MX.png" alt-text="Wybierz sekcję MX.":::

1. Na stronie Dodawanie rekordu DNS w polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli.

    |Nazwa hosta|Wskazuje na|Priority (Priorytet)|TTL (Czas wygaśnięcia)|
    |---|---|---|---|
    |@|*\<domain-key\>*.mail.protection.outlook.com  <br/>  UWAGA: Pobierz dane \<domain-key\> z konta Microsoft. [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)|10  <br/> Aby uzyskać więcej informacji o priorytetach, zobacz [Co to jest priorytet rekordu MX?](../setup/domains-faq.yml)|1 godzina|

1. Wybierz **Zapisz**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-MX-Save.png" alt-text="Wybierz pozycję Zapisz.":::

1. Jeśli na liście znajdują się już rekordy MX, usuń je, wybierając kosz **Usuń rekord** na stronie **Dodawanie rekordu** .

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Delete.png" alt-text="Wybierz pozycję Usuń rekord.":::

### <a name="add-the-cname-record-required-for-microsoft"></a>Dodawanie rekordu CNAME wymaganego dla firmy Microsoft

> [!NOTE]
> Jeśli zarejestrowano się w 1und1.de, [zaloguj się tutaj](https://go.microsoft.com/fwlink/?linkid=859152).

1. Aby rozpocząć, przejdź do strony domen w witrynie IONOS by 1&1, korzystając z [tego linku](https://my.1and1.com/). Zostanie wyświetlony monit o zalogowanie się.

1. Wybierz pozycję **Menu**, a następnie wybierz pozycję **Domeny i protokół SSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Wybierz pozycję Domeny i protokół SSL.":::

1. W obszarze **Akcje** dla domeny, którą chcesz zaktualizować, wybierz kontrolkę koła zębatego, a następnie wybierz pozycję **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Wybierz pozycję DNS z listy rozwijanej.":::

   Teraz utworzysz dwie poddomeny i ustawisz wartość **lias** dla każdej z nich.

   (Jest to wymagane, ponieważ 1&1 IONOS obsługuje tylko jeden rekord CNAME najwyższego poziomu, ale firma Microsoft wymaga kilku rekordów CNAME).

   Najpierw utworzysz poddomenę Autodiscover.

1. Wybierz pozycję **Poddomeny**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Subdomains.png" alt-text="Wybierz pozycję Poddomena.":::

1. Wybierz pozycję **Dodaj poddomenę**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-add-subdomains.png" alt-text="Wybierz pozycję Dodaj poddomeny.":::

1. W polu **Dodaj poddomenę** dla nowej poddomeny wpisz lub skopiuj i wklej tylko wartość **Dodaj poddomenę** z poniższej tabeli. (Wartość **Alias** dodasz w kolejnym kroku).

    |Dodawanie poddomeny|Alias|
    |---|---|
    |autodiscover|autodiscover.outlook.com|

1. W obszarze **Akcje** dla właśnie utworzonej poddomeny **wykrywania automatycznego** wybierz kontrolkę koła zębatego, a następnie wybierz pozycję **DNS** z listy rozwijanej.

1. Wybierz pozycję **Dodaj rekord**, a następnie wybierz sekcję **CNAME** .

1. W polu **Alias** wpisz lub skopiuj i wklej tylko wartość **Alias** z poniższej tabeli.

    |Dodawanie poddomeny|Alias|
    |---|---|
    |autodiscover|autodiscover.outlook.com|

1. Wybierz **Zapisz**.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Dodawanie rekordu TXT SPF w celu zapobiegania spamowi w wiadomościach e-mail

> [!IMPORTANT]
> Nie można mieć więcej niż jednego rekordu TXT na rekord SPF dla domeny. Jeśli domena ma więcej niż jeden rekord SPF, może to spowodować błędy poczty e-mail, a także problemy z dostarczaniem i klasyfikacją spamu. Jeśli masz już rekord SPF dla swojej domeny, nie twórz nowego rekordu dla firmy Microsoft. Zamiast tego dodaj wymagane wartości firmy Microsoft do bieżącego rekordu, aby mieć  *jeden*  rekord SPF zawierający oba zestawy wartości. Potrzebujesz przykładów? Zapoznaj się z tymi [rekordami systemu nazw domen zewnętrznych dla firmy Microsoft](../../enterprise/external-domain-name-system-records.md). Aby zweryfikować rekord SPF, możesz użyć jednego z tych [narzędzi weryfikacjiSPF](../setup/domains-faq.yml).

> [!NOTE]
> Jeśli zarejestrowano się w 1und1.de, [zaloguj się tutaj](https://go.microsoft.com/fwlink/?linkid=859152).

1. Aby rozpocząć, przejdź do strony domen w witrynie IONOS by 1&1, korzystając z [tego linku](https://my.1and1.com/). Zostanie wyświetlony monit o zalogowanie się.

1. Wybierz pozycję **Menu**, a następnie wybierz pozycję **Domeny i protokół SSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Wybierz pozycję Domeny i protokół SSL.":::

1. W obszarze **Akcje** dla domeny, którą chcesz zaktualizować, wybierz kontrolkę koła zębatego, a następnie wybierz pozycję **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Wybierz pozycję DNS z listy rozwijanej.":::

1. Wybierz pozycję **Dodaj rekord**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Wybierz pozycję Dodaj rekord.":::

1. Wybierz sekcję **SPF (TXT** ).

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SPFTXT.png" alt-text="Wybierz sekcję SPF (TXT).":::

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli.

    |Wpisać|Nazwa hosta|Value|Czas wygaśnięcia|
    |---|---|---|---|
    |SPF (TXT)|Pozostaw to pole puste.|v=spf1 include:spf.protection.outlook.com -all  <br/> **Uwaga:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostały poprawne.|1 godzina|

1. Wybierz **Zapisz**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SPFTXT-Save.png" alt-text="Wybierz pozycję Zapisz.":::

## <a name="advanced-option-skype-for-business"></a>Opcja zaawansowana: Skype dla firm

Tę opcję należy wybrać tylko wtedy, gdy organizacja używa Skype dla firm dla usług komunikacji online, takich jak czat, połączenia konferencyjne i połączenia wideo, oprócz Microsoft Teams. Skype wymaga 4 rekordów: 2 rekordy SRV do komunikacji między użytkownikami i 2 rekordy CNAME, aby zalogować się i połączyć użytkowników z usługą.

### <a name="add-two-additional-cname-records"></a>Dodawanie dwóch dodatkowych rekordów CNAME

1. Aby rozpocząć, przejdź do strony domen w witrynie IONOS by 1&1, korzystając z [tego linku](https://my.1and1.com/). Zostanie wyświetlony monit o zalogowanie się.

1. Wybierz pozycję **Menu**, a następnie wybierz pozycję **Domeny i protokół SSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Wybierz pozycję Domeny i protokół SSL.":::

1. W obszarze **Akcje** dla domeny, którą chcesz zaktualizować, wybierz kontrolkę koła zębatego, a następnie wybierz pozycję **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Wybierz pozycję DNS z listy rozwijanej.":::

   Teraz utworzysz dwie poddomeny i ustawisz wartość **lias** dla każdej z nich.

   (Jest to wymagane, ponieważ 1&1 IONOS obsługuje tylko jeden rekord CNAME najwyższego poziomu, ale firma Microsoft wymaga kilku rekordów CNAME).

   Najpierw utworzysz poddomenę lyncdiscover.

1. Wybierz pozycję **Poddomeny**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Subdomains.png" alt-text="Wybierz pozycję Poddomena.":::

1. Wybierz pozycję **Dodaj poddomenę**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-add-subdomains.png" alt-text="Wybierz pozycję Dodaj poddomeny.":::

1. W polu **Dodaj poddomenę** dla nowej poddomeny wpisz lub skopiuj i wklej tylko wartość **Dodaj poddomenę** z poniższej tabeli. (Wartość **Alias** dodasz w kolejnym kroku).

    |Dodawanie poddomeny|Alias|
    |---|---|
    |lyncdiscover   |webdir.online.lync.com  |

1. W obszarze **Akcje** dla właśnie utworzonej poddomeny **lyncdiscover** wybierz kontrolkę koła zębatego, a następnie wybierz pozycję **DNS** z listy rozwijanej.

1. Wybierz pozycję **Dodaj rekord**, a następnie wybierz sekcję **CNAME** .

1. W polu **Alias** wpisz lub skopiuj i wklej tylko wartość **Alias** z poniższej tabeli.

    |Create Subdomain (Utwórz poddomenę)|Alias|
    |---|---|
    |lyncdiscover|webdir.online.lync.com|

1. Utwórz inną poddomenę (SIP): wybierz pozycję **Dodaj poddomenę**.

1. W polu **Dodaj poddomenę** dla nowej poddomeny wpisz lub skopiuj i wklej tylko wartość **Dodaj poddomenę** z poniższej tabeli. (Wartość **Alias** dodasz w kolejnym kroku).

    |Dodawanie poddomeny|Alias|
    |---|---|
    |sip|sipdir.online.lync.com|

1. W obszarze **Akcje** dla właśnie utworzonej poddomeny wybierz kontrolkę koła zębatego, a następnie wybierz pozycję **DNS** z listy rozwijanej.

1. Wybierz pozycję **Dodaj rekord**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Wybierz pozycję Dodaj rekord.":::

1. Wybierz sekcję **CNAME** .

1. w polu **Alias:** wpisz lub skopiuj i wklej tylko wartość **Alias** z poniższej tabeli.

    |Create Subdomain (Utwórz poddomenę)|Alias|
    |---|---|
    |sip|sipdir.online.lync.com|

1. Zaznacz pole wyboru dla zastrzeżenia **O mnie** , a następnie wybierz pozycję **Zapisz**.

## <a name="add-the-two-srv-records-required-for-microsoft"></a>Dodaj dwa rekordy SRV wymagane dla firmy Microsoft

> [!NOTE]
> Jeśli zarejestrowano się w 1und1.de, [zaloguj się tutaj](https://go.microsoft.com/fwlink/?linkid=859152).

1. Aby rozpocząć, przejdź do strony domen w witrynie IONOS by 1&1, korzystając z [tego linku](https://my.1and1.com/). Zostanie wyświetlony monit o zalogowanie się.

1. Wybierz pozycję **Menu**, a następnie wybierz pozycję **Domeny i protokół SSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Wybierz pozycję Domeny i protokół SSL.":::

1. W obszarze **Akcje** dla domeny, którą chcesz zaktualizować, wybierz kontrolkę koła zębatego, a następnie wybierz pozycję **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Wybierz pozycję DNS z listy rozwijanej.":::

1. Wybierz pozycję **Dodaj rekord**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Wybierz pozycję Dodaj rekord.":::

1. Wybierz sekcję **SRV** .

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SRV.png" alt-text="Wybierz sekcję SRV.":::

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli.

    |Wpisać|Usługa|Protocol (Protokół)|Nazwa hosta|Wskazuje na|Priority (Priorytet)|Waga|Port|Czas wygaśnięcia|
    |---|---|---|---|---|---|---|---|---|
    |SRV|_sip|tls|Pozostaw to pole puste.|sipdir.online.lync.com|100|1|443|1 godzina|
    |SRV|_sipfederationtls|tcp|Pozostaw to pole puste.|sipfed.online.lync.com|100|1|5061|1 godzina|

1. Wybierz **Zapisz**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SRV-Save.png" alt-text="Wybierz pozycję Zapisz.":::

1. Dodaj drugi rekord SRV.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli masz problemy z przepływem poczty lub inne problemy po dodaniu rekordów DNS, zobacz [Znajdowanie i rozwiązywanie problemów po dodaniu domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Opcja zaawansowana: Intune i mobile Zarządzanie urządzeniami dla Microsoft 365

Ta usługa ułatwia zabezpieczanie i zdalne zarządzanie urządzeniami przenośnymi łączącymi się z domeną. Usługa Mobile Zarządzanie urządzeniami wymaga 2 rekordów CNAME, aby użytkownicy mogli rejestrować urządzenia w usłudze.

### <a name="add-the-two-required-cname-records"></a>Dodawanie dwóch wymaganych rekordów CNAME

> [!IMPORTANT]
> Postępuj zgodnie z procedurą poddomeny użytą dla innych rekordów CNAME i podaj wartości z poniższej tabeli.

1. Aby rozpocząć, przejdź do strony domen w witrynie IONOS by 1&1, korzystając z [tego linku](https://my.1and1.com/). Zostanie wyświetlony monit o zalogowanie się.

1. Wybierz pozycję **Menu**, a następnie wybierz pozycję **Domeny i protokół SSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Wybierz pozycję Domeny i protokół SSL.":::

1. W obszarze **Akcje** dla domeny, którą chcesz zaktualizować, wybierz kontrolkę koła zębatego, a następnie wybierz pozycję **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Wybierz pozycję DNS z listy rozwijanej.":::

   Teraz utworzysz dwie poddomeny i ustawisz wartość **lias** dla każdej z nich.

   (Jest to wymagane, ponieważ 1&1 IONOS obsługuje tylko jeden rekord CNAME najwyższego poziomu, ale firma Microsoft wymaga kilku rekordów CNAME).

   Najpierw utworzysz poddomenę lyncdiscover.

1. Wybierz pozycję **Poddomeny**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Subdomains.png" alt-text="Wybierz pozycję Poddomena.":::

1. Wybierz pozycję **Dodaj poddomenę**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-add-subdomains.png" alt-text="Wybierz pozycję Dodaj poddomeny.":::

1. W polu **Dodaj poddomenę** dla nowej poddomeny wpisz lub skopiuj i wklej tylko wartość **Dodaj poddomenę** z poniższej tabeli. (Wartość **Alias** dodasz w kolejnym kroku).

    |Dodawanie poddomeny|Alias|
    |---|---|
    |enterpriseregistration|enterpriseregistration.windows.net|

1. W obszarze **Akcje** dla właśnie utworzonej poddomeny **enterpriseregistration** wybierz kontrolkę koła zębatego, a następnie wybierz pozycję **DNS** z listy rozwijanej.

1. Wybierz pozycję **Dodaj rekord**, a następnie wybierz sekcję **CNAME** .

1. W polu **Alias** wpisz lub skopiuj i wklej tylko wartość **Alias** z poniższej tabeli.

    |Dodawanie poddomeny|Alias|
    |---|---|
    |enterpriseregistration|enterpriseregistration.windows.net|

1. Utwórz inną poddomenę: wybierz pozycję **Dodaj poddomenę**.

1. W polu **Dodaj poddomenę** dla nowej poddomeny wpisz lub skopiuj i wklej tylko wartość **Dodaj poddomenę** z poniższej tabeli. (Wartość **Alias** dodasz w kolejnym kroku).

    |Dodawanie poddomeny|Alias|
    |---|---|
    |enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com|

1. W obszarze **Akcje** dla właśnie utworzonej **poddomeny enterpriseenrollment** wybierz kontrolkę koła zębatego, a następnie wybierz pozycję **DNS** z listy rozwijanej.

1. Wybierz pozycję **Dodaj rekord**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Wybierz pozycję Dodaj rekord.":::

1. Wybierz sekcję **CNAME** .

1. w polu **Alias:** wpisz lub skopiuj i wklej tylko wartość **Alias** z poniższej tabeli.

    |Create Subdomain (Utwórz poddomenę)|Alias|
    |---|---|
    |enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com|

1. Zaznacz pole wyboru dla zastrzeżenia **O mnie** , a następnie wybierz pozycję **Zapisz**.
