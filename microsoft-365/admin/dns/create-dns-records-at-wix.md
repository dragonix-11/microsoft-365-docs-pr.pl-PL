---
title: Połączenie rekordy DNS w systemie Wix do Microsoft 365
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
description: Dowiedz się, jak zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, Skype dla firm Online i innych usług w aplikacji Wix for Microsoft.
ms.openlocfilehash: 58d7819e006183a35272811ed791d3236f9fc742
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780325"
---
# <a name="connect-your-dns-records-at-wix-to-microsoft-365"></a>Połączenie rekordy DNS w systemie Wix do Microsoft 365

**[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji.

Jeśli Wix jest dostawcą hostingu DNS, wykonaj kroki opisane w tym artykule, aby zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, Skype dla firm Online itd.

Po dodaniu tych rekordów w programie Wix domena zostanie skonfigurowana do pracy z usługi firmy Microsoft.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-a-txt-record-for-verification"></a>Dodawanie rekordu TXT w celu weryfikacji

Przed użyciem domeny z firmą Microsoft musimy upewnić się, że jesteś jej właścicielem. Możliwość zalogowania się do konta u rejestratora domen i utworzenia rekordu DNS potwierdza firmie Microsoft, że jesteś właścicielem domeny.

> [!NOTE]
> Ten rekord jest używany tylko do weryfikowania, że jesteś właścicielem domeny, i nie wywiera wpływu na nic innego. Możesz usunąć go później, jeśli chcesz.

> [!NOTE]
> WIX nie obsługuje wpisów DNS dla poddomen.

1. Aby rozpocząć, przejdź do strony domen w witrynie Wix, korzystając z [tego linku](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Zostanie wyświetlony monit o zalogowanie się.

2. Wybierz pozycję **Domeny** \> **...**, a następnie wybierz pozycję **Zarządzaj rekordami DNS** z listy rozwijanej.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Wybierz pozycję Zarządzaj rekordami DNS z listy rozwijanej.":::

3. Wybierz pozycję **+ Dodaj rekord** w wierszu **TXT (Tekst)** edytora DNS.

   :::image type="content" source="../../media/dns-wix/wix-domains-TXT-add-record.png" alt-text="Wybierz pozycję Dodaj rekord.":::

4. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli.

   |Nazwa hosta|Wartość TXT|Czas wygaśnięcia|
   |---|---|---|
   |Automatycznie wypełnione (pozostaw puste)|MS=*msXXXXXXXXXX* <br/> **Uwaga:** Jest to przykład. W tym miejscu użyj określonej wartości **Destination (Miejsce docelowe) lub Points to Address (Punkty do adresu** ) z tabeli . [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)|1 godzina|

5. Wybierz **pozycjęZapisz**.

   :::image type="content" source="../../media/dns-wix/wix-domains-txt-save.png" alt-text="Wybierz pozycję Zapisz.":::

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

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Dodaj rekord MX, aby wiadomość e-mail dla twojej domeny przyszła do firmy Microsoft

1. Aby rozpocząć, przejdź do strony domen w witrynie Wix, korzystając z [tego linku](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Zostanie wyświetlony monit o zalogowanie się.

1. Wybierz pozycję **Domeny** \> **...**, a następnie wybierz pozycję **Zarządzaj rekordami DNS** z listy rozwijanej.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Wybierz pozycję Zarządzaj rekordami DNS z listy rozwijanej.":::

1. W obszarze **MX (Wymiana poczty)** wybierz pozycję **Edytuj rekordy MX**.

   :::image type="content" source="../../media/dns-wix/wix-domains-edit-mx-records.png" alt-text="Wybierz pozycję Edytuj rekordy MX.":::

1. Wybierz pozycję **Inne** z listy rozwijanej, a następnie wybierz pozycję **+ Dodaj rekord**.

   :::image type="content" source="../../media/dns-wix/wix-domains-other.png" alt-text="Wybierz pozycję Inne z listy rozwijanej.":::

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli:

   |Nazwa hosta|Wskazuje na|Priority (Priorytet)|TTL (Czas wygaśnięcia)|
   |---|---|---|---|
   |Automatycznie wypełnione|*\<domain-key\>*.mail.protection.outlook.com <br/> **Uwaga:** Pobierz dane *\<domain-key\>* z konta Microsoft.  [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)|0 <br/> Aby uzyskać więcej informacji o priorytetach, zobacz [Co to jest priorytet rekordu MX?](../setup/domains-faq.yml)|1 godzina|

1. Jeśli na liście znajdują się inne rekordy MX, usuń każdy z nich.

  :::image type="content" source="../../media/dns-wix/wix-domains-mx-delete.png" alt-text="Wybierz pozycję Usuń.":::

1. Wybierz **Zapisz**.

## <a name="add-the-cname-record-required-for-microsoft"></a>Dodawanie rekordu CNAME wymaganego dla firmy Microsoft

1. Aby rozpocząć, przejdź do strony domen w witrynie Wix, korzystając z [tego linku](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Zostanie wyświetlony monit o zalogowanie się.

2. Wybierz pozycję **Domeny** \> **...**, a następnie wybierz pozycję **Zarządzaj rekordami DNS** z listy rozwijanej.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Wybierz pozycję Zarządzaj rekordami DNS z listy rozwijanej.":::

3. Wybierz pozycję **+ Dodaj rekord** w wierszu **CNAME (Aliasy)** edytora DNS dla rekordu CNAME.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-add-record.png" alt-text="Wybierz pozycję + Dodaj rekord.":::

4. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli:

   |Nazwa hosta|Value|Czas wygaśnięcia|
   |---|---|---|
   |autodiscover|autodiscover.outlook.com|1 godzina|

5. Wybierz **Zapisz**.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="Wybierz pozycję Zapisz.":::

   Przed kontynuowaniem poczekaj kilka minut na zaktualizowanie utworzonego właśnie rekordu w Internecie.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Dodawanie rekordu TXT SPF w celu zapobiegania spamowi w wiadomościach e-mail

> [!IMPORTANT]
> Nie można mieć więcej niż jednego rekordu TXT na rekord SPF dla domeny. Jeśli domena ma więcej niż jeden rekord SPF, może to spowodować błędy poczty e-mail, a także problemy z dostarczaniem i klasyfikacją spamu. Jeśli masz już rekord SPF dla swojej domeny, nie twórz nowego rekordu dla firmy Microsoft. Zamiast tego dodaj wymagane wartości firmy Microsoft do bieżącego rekordu, aby mieć *jeden* rekord SPF zawierający oba zestawy wartości.

1. Aby rozpocząć, przejdź do strony domen w witrynie Wix, korzystając z [tego linku](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Zostanie wyświetlony monit o zalogowanie się.

2. Wybierz pozycję **Domeny** \> **...**, a następnie wybierz pozycję **Zarządzaj rekordami DNS** z listy rozwijanej.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Wybierz pozycję Zarządzaj rekordami DNS z listy rozwijanej.":::

3. Wybierz pozycję **+ Dodaj rekord** w wierszu **TXT (Tekst)** edytora DNS.

   :::image type="content" source="../../media/dns-wix/wix-domains-TXT-add-record.png" alt-text="Wybierz pozycję + Dodaj rekord.":::

   **Uwaga**: Wix udostępnia wiersz SPF w edytorze DNS. Zignoruj ten wiersz i użyj **wiersza TXT (Tekst),** aby wprowadzić poniższe wartości SPF.

4. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli:

   |Nazwa hosta|Value|Czas wygaśnięcia|
   |---|---|---|
   |[pozostaw to puste]|v=spf1 include:spf.protection.outlook.com -all <br/> **Uwaga:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostały poprawne.|1 godzina|

5. Wybierz **Zapisz**.

   :::image type="content" source="../../media/dns-wix/wix-domains-txt-save.png" alt-text="Wybierz pozycję Zapisz.":::

   Przed kontynuowaniem poczekaj kilka minut na zaktualizowanie utworzonego właśnie rekordu w Internecie.

## <a name="advanced-option-skype-for-business"></a>Opcja zaawansowana: Skype dla firm

Tę opcję należy wybrać tylko wtedy, gdy organizacja używa Skype dla firm dla usług komunikacji online, takich jak czat, połączenia konferencyjne i połączenia wideo, oprócz Microsoft Teams. Skype potrzebuje czterech rekordów: dwóch rekordów SRV na potrzeby komunikacji między użytkownikami i dwóch rekordów CNAME, aby zalogować się i połączyć użytkowników z usługą.

### <a name="add-the-two-required-srv-records"></a>Dodawanie dwóch wymaganych rekordów SRV

1. Aby rozpocząć, przejdź do strony domen w witrynie Wix, korzystając z [tego linku](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Zostanie wyświetlony monit o zalogowanie się.

1. Wybierz pozycję **Domeny** \> **...**, a następnie wybierz pozycję **Zarządzaj rekordami DNS** z listy rozwijanej.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Wybierz pozycję Zarządzaj rekordami DNS z listy rozwijanej.":::

1. Wybierz pozycję **+ Dodaj rekord** w wierszu **SRV** edytora DNS.

   :::image type="content" source="../../media/dns-wix/wix-domains-srv-add-record.png" alt-text="Wybierz pozycję + Dodaj rekord.":::

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z pierwszego wiersza w tabeli:

   |Usługa|Protocol (Protokół)|Nazwa hosta|Waga|Port|Target (Element docelowy)|Priority (Priorytet)|TTL (Czas wygaśnięcia)|
   |---|---|---|---|---|---|---|---|
   |sip|tls|Automatycznie wypełnione|1|443|sipdir.online.lync.com|100|1 godzina|
   |sipfed|tcp|Automatycznie wypełnione|1|5061|sipfed.online.lync.com|100|1 godzina|

1. Wybierz **Zapisz**.

   :::image type="content" source="../../media/dns-wix/wix-domains-srv-save.png" alt-text="Wybierz pozycję Zapisz.":::

1. Dodaj inny rekord SRV, kopiując wartości z drugiego wiersza tabeli.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli masz problemy z przepływem poczty lub inne problemy po dodaniu rekordów DNS, zobacz [Znajdowanie i rozwiązywanie problemów po dodaniu domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Dodaj dwa wymagane rekordy CNAME dla Skype dla firm

1. Wybierz pozycję **+ Dodaj kolejny** w wierszu **CNAME (Aliasy)** edytora DNS i wprowadź wartości z pierwszego wiersza w poniższej tabeli.

   |Wpisać|Host|Value|Czas wygaśnięcia|
   |---|---|---|---|
   |CNAME|sip|sipdir.online.lync.com. <br/> **Wartość ta MUSI mieć na końcu kropkę (.)**|1 godzina|
   |CNAME|lyncdiscover|webdir.online.lync.com. <br/> **Wartość ta MUSI mieć na końcu kropkę (.)**|1 godzina|

1. Wybierz **Zapisz**.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="Wybierz pozycję Zapisz.":::

1. Dodaj inny rekord CNAME, kopiując wartości z drugiego wiersza tabeli.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Opcja zaawansowana: Intune i mobile Zarządzanie urządzeniami dla Microsoft 365

Ta usługa ułatwia zabezpieczanie i zdalne zarządzanie urządzeniami przenośnymi łączącymi się z domeną. Usługa Mobile Zarządzanie urządzeniami wymaga dwóch rekordów CNAME, aby użytkownicy mogli rejestrować urządzenia w usłudze.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Dodaj dwa wymagane rekordy CNAME dla usługi Mobile Zarządzanie urządzeniami

1. Aby rozpocząć, przejdź do strony domen w witrynie Wix, korzystając z [tego linku](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Zostanie wyświetlony monit o zalogowanie się.

1. Wybierz pozycję **Domeny** \> **...**, a następnie wybierz pozycję **Zarządzaj rekordami DNS** z listy rozwijanej.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Wybierz pozycję Zarządzaj rekordami DNS z listy rozwijanej.":::

1. Wybierz pozycję **+ Dodaj rekord** w wierszu **CNAME (Aliasy)** edytora DNS dla rekordu CNAME.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-add-record.png" alt-text="Wybierz pozycję + Dodaj rekord.":::

1. Wprowadź wartości z pierwszego wiersza w poniższej tabeli.

    |Wpisać|Host|Value|Czas wygaśnięcia|
    |---|---|---|---|
    |CNAME|enterpriseregistration|enterpriseregistration.windows.net. <br/> **Wartość ta MUSI mieć na końcu kropkę (.)**|1 godzina|
    |CNAME|enterpriseenrollment|enterpriseenrollment.manage.microsoft.com. <br/> **Wartość ta MUSI mieć na końcu kropkę (.)**|1 godzina|

1. Wybierz **Zapisz**.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="Wybierz pozycję Zapisz.":::

1. Dodaj inny rekord CNAME, kopiując wartości z drugiego wiersza tabeli.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).
