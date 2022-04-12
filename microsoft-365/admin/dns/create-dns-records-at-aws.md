---
title: Połączenie rekordy DNS w usłudze Amazon Web Services (AWS) w celu Microsoft 365
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
ms.assetid: 7a2efd75-0771-4897-ba7b-082fe5bfa9da
description: Dowiedz się, jak zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, Skype dla firm Online i innych usług w usługach Amazon Web Services (AWS) dla firmy Microsoft.
ms.openlocfilehash: d194e425485a45d2c3dc949fc85e74bc957932fb
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780660"
---
# <a name="connect-your-dns-records-at-amazon-web-services-aws-to-microsoft-365"></a>Połączenie rekordy DNS w usłudze Amazon Web Services (AWS) w celu Microsoft 365

 **[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji.

Jeśli platforma AWS jest dostawcą hostingu DNS, wykonaj kroki opisane w tym artykule, aby zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, Skype online dla firm itd.

Po dodaniu tych rekordów na platformie AWS domena zostanie skonfigurowana do pracy z usługi firmy Microsoft.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli masz problemy z przepływem poczty lub inne problemy po dodaniu rekordów DNS, zobacz [Znajdowanie i rozwiązywanie problemów po dodaniu domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-a-txt-record-for-verification"></a>Dodawanie rekordu TXT w celu weryfikacji

Przed użyciem domeny z firmą Microsoft musimy upewnić się, że jesteś jej właścicielem. Możliwość zalogowania się do konta u rejestratora domen i utworzenia rekordu DNS potwierdza firmie Microsoft, że jesteś właścicielem domeny.

> [!NOTE]
> Ten rekord jest używany tylko do weryfikowania, że jesteś właścicielem domeny, i nie wywiera wpływu na nic innego. Jeśli chcesz, możesz go później usunąć.

1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie AWS, używając [tego linku](https://console.aws.amazon.com/route53/home). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie docelowej w obszarze **Domeny** wybierz pozycję **Zarejestrowane domeny**.

1. W obszarze **Nazwa domeny** wybierz domenę, którą chcesz skonfigurować w Microsoft 365.

    **Uwaga**: Jeśli nie utworzono strefy hostowanej dla domeny, wybierz pozycję **Utwórz hostowaną strefę** i wykonaj kroki przed przejściem do następnego kroku.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Wybierz nazwę domeny, którą chcesz zweryfikować.":::

1. Wybierz pozycję **Zarządzaj systemem DNS**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Wybierz pozycję Zarządzaj systemem DNS z listy rozwijanej.":::

1. W obszarze **Nazwa domeny** wybierz nazwę domeny dla wersji strefy hostowanej domeny, którą chcesz zweryfikować.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Wybierz nazwę domeny, którą chcesz zweryfikować.":::

1. Wybierz pozycję **Utwórz rekord**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Wybierz pozycję Utwórz rekord.":::

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli.

    (Wybierz wartości zasad **Typ** i **Routing** z list rozwijanych).

    > [!TIP]
    > Znaki cudzysłowu wymagane w instrukcjach wyświetlanych na ekranie zostaną wprowadzone automatycznie. Nie musisz wpisywać ich ręcznie.

    |Nazwa rekordu|Typ rekordu|Value|TTL (Seconds) [Czas wygaśnięcia (w sekundach)]|Zasady routingu|
    |:-----|:-----|:-----|:-----|:-----|
    |Pozostaw to pole puste.|TXT — służy do weryfikowania nadawców wiadomości e-mail|MS=*msXXXXXXXXXX* <br/> **Uwaga:** Jest to przykład. Tutaj użyj określonej wartości **Miejsce docelowe lub Punkt-adres** z tabeli w Microsoft 365. [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)|300|Simple (Proste)|

1. Wybierz pozycję **Utwórz rekordy**.

   :::image type="content" source="../../media/dns-aws/aws-domains-txt-create-records.png" alt-text="Wybierz pozycję Utwórz rekordy.":::

   Przed kontynuowaniem poczekaj kilka minut na zaktualizowanie utworzonego właśnie rekordu w Internecie.

Po dodaniu rekordu w witrynie rejestratora domen wrócisz do firmy Microsoft i zażądasz wyszukania rekordu. Gdy firma Microsoft znajdzie właściwy rekord TXT, domena zostanie zweryfikowana.

Aby zweryfikować rekord w Microsoft 365:

1. W centrum administracyjnym przejdź do **obszaru domeny Ustawienia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**.**</a>

1. Na stronie Domeny wybierz domenę, którą weryfikujesz, a następnie wybierz pozycję **Rozpocznij konfigurację**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Wybierz pozycję Rozpocznij konfigurację.":::

1. Wybierz pozycję **Kontynuuj**.

1. Na stronie **Weryfikowanie domeny** wybierz pozycję **Weryfikuj**.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli masz problemy z przepływem poczty lub inne problemy po dodaniu rekordów DNS, zobacz [Znajdowanie i rozwiązywanie problemów po dodaniu domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft-365"></a>Dodaj rekord MX, aby wiadomość e-mail dla twojej domeny była wysyłana do Microsoft 365

1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie AWS, używając [tego linku](https://console.aws.amazon.com/route53/home). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie docelowej w obszarze **Domeny** wybierz pozycję **Zarejestrowane domeny**.

1. W obszarze **Nazwa domeny** wybierz domenę, którą chcesz skonfigurować w Microsoft 365.

    **Uwaga**: Jeśli nie utworzono strefy hostowanej dla domeny, wybierz pozycję **Utwórz hostowaną strefę** i wykonaj kroki przed przejściem do następnego kroku.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Wybierz nazwę domeny.":::

1. Wybierz pozycję **Zarządzaj systemem DNS**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Wybierz pozycję Zarządzaj systemem DNS z listy rozwijanej.":::

1. W obszarze **Nazwa domeny** wybierz nazwę domeny dla wersji strefy hostowanej domeny, którą chcesz zweryfikować.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Wybierz nazwę domeny.":::

1. Wybierz pozycję **Utwórz rekord**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Wybierz pozycję Utwórz rekord.":::

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli.

    (Wybierz wartości zasad **Typ** i **Routing** z list rozwijanych).

    > [!TIP]
    > Znaki cudzysłowu wymagane w instrukcjach wyświetlanych na ekranie zostaną wprowadzone automatycznie. Nie musisz wpisywać ich ręcznie.

    |Nazwa rekordu|Typ rekordu|Value|TTL (Seconds) [Czas wygaśnięcia (w sekundach)]|Zasady routingu|
    |:-----|:-----|:-----|:-----|:-----|
    |Pozostaw to pole puste.|MX — określa serwery poczty|0 *\<domain-key\>*.mail.protection.outlook.com. <br/> 0 to wartość priorytetu rekordu MX. Dodaj ją na początku wartości MX i oddziel ją od reszty wartości spacją.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> **Uwaga:** Pobierz dane \<*domain-key*\> z konta Microsoft 365. [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)|300|Prosty routing|

1. Wybierz pozycję **Utwórz rekordy**.

   :::image type="content" source="../../media/dns-aws/aws-domains-mx-create-records.png" alt-text="Wybierz pozycję Utwórz rekordy.":::

1. Jeśli istnieją inne rekordy MX, usuń je, wybierając rekord, a następnie wybierając pozycję **Usuń**.

## <a name="add-the-cname-record-required-for-microsoft-365"></a>Dodaj rekord CNAME wymagany dla Microsoft 365

1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie AWS, używając [tego linku](https://console.aws.amazon.com/route53/home). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie docelowej w obszarze **Domeny** wybierz pozycję **Zarejestrowane domeny**.

1. W obszarze **Nazwa domeny** wybierz domenę, którą chcesz skonfigurować w Microsoft 365.

    **Uwaga**: Jeśli nie utworzono strefy hostowanej dla domeny, wybierz pozycję **Utwórz hostowaną strefę** i wykonaj kroki przed przejściem do następnego kroku.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Wybierz nazwę domeny.":::

1. Wybierz pozycję **Zarządzaj systemem DNS**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Wybierz pozycję Zarządzaj systemem DNS z listy rozwijanej.":::

1. W obszarze **Nazwa domeny** wybierz nazwę domeny dla wersji strefy hostowanej domeny, którą chcesz zweryfikować.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Wybierz nazwę domeny.":::

1. Wybierz pozycję **Utwórz rekord**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Wybierz pozycję Utwórz rekord.":::

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli.

    (Wybierz wartości zasad **Typ** i **Routing** z list rozwijanych).

    |Nazwa rekordu|Typ rekordu|Value|Czas wygaśnięcia|Zasady routingu|
    |:-----|:-----|:-----|:-----|:-----|
    |autodiscover|CNAME — kieruje ruch do innej nazwy domeny|autodiscover.outlook.com. <br/> **Wartość ta MUSI mieć na końcu kropkę (.)**|300|Simple (Proste)|

1. Wybierz pozycję **Utwórz rekordy**.

   :::image type="content" source="../../media/dns-aws/aws-domains-cname-create-records.png" alt-text="Wybierz pozycję Utwórz rekordy.":::

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Dodawanie rekordu TXT SPF w celu zapobiegania spamowi w wiadomościach e-mail

> [!IMPORTANT]
> Nie można mieć więcej niż jednego rekordu TXT na rekord SPF dla domeny. Jeśli domena ma więcej niż jeden rekord SPF, może to spowodować błędy poczty e-mail, a także problemy z dostarczaniem i klasyfikacją spamu. Jeśli masz już rekord SPF dla swojej domeny, nie twórz nowego rekordu dla firmy Microsoft. Zamiast tego dodaj wymagane wartości firmy Microsoft do bieżącego rekordu, aby mieć *jeden* rekord SPF zawierający oba zestawy wartości. Potrzebujesz przykładów? Zapoznaj się z tymi [rekordami systemu nazw domen zewnętrznych dla firmy Microsoft](../../enterprise/external-domain-name-system-records.md). Aby zweryfikować rekord SPF, możesz użyć jednego z tych [narzędzi weryfikacjiSPF](../setup/domains-faq.yml).

1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie AWS, używając [tego linku](https://console.aws.amazon.com/route53/home). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie docelowej w obszarze **Domeny** wybierz pozycję **Zarejestrowane domeny**.

1. W obszarze **Nazwa domeny** wybierz domenę, którą chcesz skonfigurować w Microsoft 365.

    **Uwaga**: Jeśli nie utworzono strefy hostowanej dla domeny, wybierz pozycję **Utwórz hostowaną strefę** i wykonaj kroki przed przejściem do następnego kroku.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Wybierz nazwę domeny.":::

1. Wybierz pozycję **Zarządzaj systemem DNS**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Wybierz pozycję Zarządzaj systemem DNS z listy rozwijanej.":::

1. W obszarze **Nazwa domeny** wybierz nazwę domeny dla wersji strefy hostowanej domeny, którą chcesz zweryfikować.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Wybierz nazwę domeny.":::

1. Wybierz pozycję **Utwórz rekord**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Wybierz pozycję Utwórz rekord.":::

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli.

    (Wybierz wartość **Typ** z list rozwijanych).

    |Typ rekordu|Value|
    |:-----|:-----|
    |TXT — służy do weryfikowania nadawców wiadomości e-mail i wartości specyficznych dla aplikacji|v=spf1 include:spf.protection.outlook.com -all <br/> Znaki cudzysłowu wymagane w instrukcjach wyświetlanych na ekranie zostaną wprowadzone automatycznie. Nie musisz wpisywać ich ręcznie.  <br/> **Uwaga:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostały poprawne.|

1. Wybierz pozycję **Utwórz rekordy**.

   :::image type="content" source="../../media/dns-aws/aws-domains-txt-create-records.png" alt-text="Wybierz pozycję Utwórz rekordy.":::

## <a name="advanced-option-skype-for-business"></a>Opcja zaawansowana: Skype dla firm

Tę opcję należy wybrać tylko wtedy, gdy organizacja używa Skype dla firm dla usług komunikacji online, takich jak czat, połączenia konferencyjne i połączenia wideo, oprócz Microsoft Teams. Skype wymaga 4 rekordów: 2 rekordy SRV do komunikacji między użytkownikami i 2 rekordy CNAME, aby zalogować się i połączyć użytkowników z usługą.

### <a name="add-the-two-required-srv-records"></a>Dodawanie dwóch wymaganych rekordów SRV

1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie AWS, używając [tego linku](https://console.aws.amazon.com/route53/home). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie docelowej w obszarze **Domeny** wybierz pozycję **Zarejestrowane domeny**.

1. W obszarze **Nazwa domeny** wybierz domenę, którą chcesz skonfigurować w Microsoft 365.

    **Uwaga**: Jeśli nie utworzono strefy hostowanej dla domeny, wybierz pozycję **Utwórz hostowaną strefę** i wykonaj kroki przed przejściem do następnego kroku.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Wybierz nazwę domeny.":::

1. Wybierz pozycję **Zarządzaj systemem DNS**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Wybierz pozycję Zarządzaj systemem DNS z listy rozwijanej.":::

1. W obszarze **Nazwa domeny** wybierz nazwę domeny dla wersji strefy hostowanej domeny, którą chcesz zweryfikować.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Wybierz nazwę domeny.":::

1. Wybierz pozycję **Utwórz rekord**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Wybierz pozycję Utwórz rekord.":::

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli.

    Z list rozwijanych wybierz wartości **Type** (Typ) i **Routing Policy** (Zasady routingu).

    |Nazwa rekordu|Typ rekordu|Value|TTL (Seconds) [Czas wygaśnięcia (w sekundach)]|Zasady routingu|
    |:-----|:-----|:-----|:-----|:-----|
    |_sip._tls|SRV — wartości specyficzne dla aplikacji, których identyfikatory dotyczą serwerów|100 1 443 sipdir.online.lync.com. **Ta wartość MUSI kończyć się kropką (.)**> <br/> **Uwaga:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostały poprawne.|300|Simple (Proste)|
    |_sipfederationtls._tcp|SRV — wartości specyficzne dla aplikacji, których identyfikatory dotyczą serwerów|100 1 5061 sipfed.online.lync.com. **Wartość ta MUSI mieć na końcu kropkę (.)** <br/> **Uwaga:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostały poprawne.|300|Simple (Proste)|

1. Aby dodać inny rekord SRV, wybierz pozycję **Dodaj kolejny rekord**, utwórz rekord przy użyciu wartości z następnego wiersza w tabeli, a następnie ponownie wybierz pozycję **Utwórz rekordy**.

   :::image type="content" source="../../media/dns-aws/aws-domians-srv-create-records.png" alt-text="Wybierz pozycję Utwórz rekordy.":::

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli masz problemy z przepływem poczty lub inne problemy po dodaniu rekordów DNS, zobacz [Znajdowanie i rozwiązywanie problemów po dodaniu domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Dodaj dwa wymagane rekordy CNAME dla Skype dla firm

1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie AWS, używając [tego linku](https://console.aws.amazon.com/route53/home). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie docelowej w obszarze **Domeny** wybierz pozycję **Zarejestrowane domeny**.

1. W obszarze **Nazwa domeny** wybierz domenę, którą chcesz skonfigurować w Microsoft 365.

    **Uwaga**: Jeśli nie utworzono strefy hostowanej dla domeny, wybierz pozycję **Utwórz hostowaną strefę** i wykonaj kroki przed przejściem do następnego kroku.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Wybierz nazwę domeny.":::

1. Wybierz pozycję **Zarządzaj systemem DNS**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Wybierz pozycję Zarządzaj systemem DNS z listy rozwijanej.":::

1. W obszarze **Nazwa domeny** wybierz nazwę domeny dla wersji strefy hostowanej domeny, którą chcesz zweryfikować.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Wybierz nazwę domeny.":::

1. Wybierz pozycję **Utwórz rekord**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Wybierz pozycję Utwórz rekord.":::

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli.

    (Wybierz wartości zasad **Typ** i **Routing** z list rozwijanych).

    |Nazwa rekordu|Typ rekordu|Value|Czas wygaśnięcia|Zasady routingu|
    |:-----|:-----|:-----|:-----|:-----|
    |sip|CNAME  Canonical name (CNAME  Nazwa kanoniczna)|sipdir.online.lync.com. <br/> **Wartość ta MUSI mieć na końcu kropkę (.)**|300|Simple (Proste)|
    |lyncdiscover|CNAME  Canonical name (CNAME  Nazwa kanoniczna)|webdir.online.lync.com. <br/> **Wartość ta MUSI mieć na końcu kropkę (.)**|300|Simple (Proste)|

1. Aby dodać inny rekord CNAME, wybierz pozycję **Dodaj inny rekord**, utwórz rekord przy użyciu wartości z następnego wiersza w tabeli.

1. Wybierz pozycję **Utwórz rekordy**.

   :::image type="content" source="../../media/dns-aws/aws-domains-cname-create-records.png" alt-text="Wybierz pozycję Utwórz rekordy.":::

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Opcja zaawansowana: Intune i mobile Zarządzanie urządzeniami dla Microsoft 365

Ta usługa ułatwia zabezpieczanie i zdalne zarządzanie urządzeniami przenośnymi łączącymi się z domeną. Usługa Mobile Zarządzanie urządzeniami wymaga dwóch rekordów CNAME, aby użytkownicy mogli rejestrować urządzenia w usłudze.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Dodaj dwa wymagane rekordy CNAME dla usługi Mobile Zarządzanie urządzeniami

1. Aby rozpocząć pracę, przejdź do swojej strony domen w witrynie AWS, używając [tego linku](https://console.aws.amazon.com/route53/home). Zostanie wyświetlony monit o zalogowanie się.

1. Na stronie docelowej w obszarze **Domeny** wybierz pozycję **Zarejestrowane domeny**.

1. W obszarze **Nazwa domeny** wybierz domenę, którą chcesz skonfigurować w Microsoft 365.

    **Uwaga**: Jeśli nie utworzono strefy hostowanej dla domeny, wybierz pozycję **Utwórz hostowaną strefę** i wykonaj kroki przed przejściem do następnego kroku.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Wybierz nazwę domeny.":::

1. Wybierz pozycję **Zarządzaj systemem DNS**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Wybierz pozycję Zarządzaj systemem DNS z listy rozwijanej.":::

1. W obszarze **Nazwa domeny** wybierz nazwę domeny dla wersji strefy hostowanej domeny, którą chcesz zweryfikować.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Wybierz nazwę domeny.":::

1. Wybierz pozycję **Utwórz rekord**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Wybierz pozycję Utwórz rekord.":::

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli.

    (Wybierz wartości zasad **Typ** i **Routing** z list rozwijanych).

    |Nazwa rekordu|Typ rekordu|Value|Czas wygaśnięcia|Zasady routingu|
    |:-----|:-----|:-----|:-----|:-----|
    |enterpriseregistration|CNAME  Canonical name (CNAME  Nazwa kanoniczna)|enterpriseregistration.windows.net. <br/> **Wartość ta MUSI mieć na końcu kropkę (.)**|300|Simple (Proste)|
    |enterpriseenrollment|CNAME  Canonical name (CNAME  Nazwa kanoniczna)|enterpriseenrollment-s.manage.microsoft.com. <br/> **Wartość ta MUSI mieć na końcu kropkę (.)**|300|Simple (Proste)|

1. Aby dodać inny rekord CNAME, wybierz pozycję **Dodaj inny rekord**, utwórz rekord przy użyciu wartości z następnego wiersza w tabeli.

1. Wybierz pozycję **Utwórz rekordy**.

   :::image type="content" source="../../media/dns-aws/aws-domains-cname-create-records.png" alt-text="Wybierz pozycję Utwórz rekordy.":::

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).
