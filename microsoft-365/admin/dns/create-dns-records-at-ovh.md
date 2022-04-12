---
title: Połączenie rekordy DNS w OVH do Microsoft 365
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
ms.assetid: 5176feef-36dc-4d84-842f-1f2b5a21ba96
description: Dowiedz się, jak zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, Skype dla firm Online i innych usług w OVH dla firmy Microsoft.
ms.openlocfilehash: 3b3174860a65d13d68b2d5f7773f927dd706f1a0
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780418"
---
# <a name="connect-your-dns-records-at-ovh-to-microsoft-365"></a>Połączenie rekordy DNS w OVH do Microsoft 365

[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml), jeśli nie możesz znaleźć szukanych informacji.

Jeśli OVH jest dostawcą hostingu DNS, wykonaj kroki opisane w tym artykule, aby zweryfikować domenę i skonfigurować rekordy DNS dla poczty e-mail, Skype dla firm Online itd.

Po dodaniu tych rekordów w OVH domena zostanie skonfigurowana do pracy z usługi firmy Microsoft.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-a-txt-record-for-verification"></a>Dodawanie rekordu TXT w celu weryfikacji

Przed użyciem domeny z firmą Microsoft musimy upewnić się, że jesteś jej właścicielem. Możliwość zalogowania się do konta u rejestratora domen i utworzenia rekordu DNS potwierdza firmie Microsoft, że jesteś właścicielem domeny.

> [!NOTE]
> Ten rekord jest używany tylko do weryfikowania, że jesteś właścicielem domeny, i nie wywiera wpływu na nic innego. Jeśli chcesz, możesz go później usunąć.

1. Aby rozpocząć, przejdź do strony domen w OVH, korzystając z [tego linku](https://www.ovh.com/manager/). Zostanie wyświetlony monit o zalogowanie się.

    ![Logowanie OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Na stronie docelowej pulpitu nawigacyjnego w obszarze **Wyświetl wszystkie moje działania** wybierz nazwę domeny, którą chcesz edytować.

1. Wybierz pozycję **Strefa DNS**.

    ![OVH Wybierz strefę DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. Wybierz **pozycję Dodaj wpis**.

    ![OVH Dodaj wpis.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. Wybierz pozycję **TXT**

    ![OVH wybierz pozycję TXT.](../../media/3aaa9dae-0b1d-436b-a980-b67a970f31a9.png)

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli. Aby przypisać wartość czasu wygaśnięcia, wybierz pozycję **Niestandardowe** z listy rozwijanej, a następnie wpisz wartość w polu tekstowym.

   |Typ rekordu|Domena podrzędna|Czas wygaśnięcia|Wartość|
   |---|---|---|---|
   |TXT|(pozostaw puste)|3600 (sekundy)|MS=msxxxxxxxxxx  <br/> **Uwaga:** Jest to przykład. W tym miejscu użyj określonej wartości **Destination (Miejsce docelowe) lub Points to Address (Punkty do adresu** ) z tabeli .  [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)|

1. Wybierz pozycję **Dalej**.

1. Wybierz pozycję **Potwierdź**.

    ![OVH potwierdź TXT do weryfikacji.](../../media/bde45596-9a55-4634-b5e7-16d7cde6e1b8.png)

1. Przed kontynuowaniem poczekaj kilka minut na zaktualizowanie utworzonego właśnie rekordu w Internecie.

Po dodaniu rekordu w witrynie rejestratora domen wrócisz do firmy Microsoft i zażądasz rekordu. Gdy firma Microsoft znajdzie właściwy rekord TXT, domena zostanie zweryfikowana.

Aby zweryfikować rekord w Microsoft 365:

1. W centrum administracyjnym przejdź do **obszaru domeny Ustawienia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**.**</a>

1. Na stronie Domeny wybierz domenę, którą weryfikujesz, a następnie wybierz pozycję **Rozpocznij konfigurację**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Wybierz pozycję Rozpocznij konfigurację.":::

1. Wybierz pozycję **Kontynuuj**.

1. Na stronie **Weryfikowanie domeny** wybierz pozycję **Weryfikuj**.

> [!NOTE]
>  Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Dodaj rekord MX, aby wiadomość e-mail dla twojej domeny przyszła do firmy Microsoft

1. Aby rozpocząć, przejdź do strony domen w OVH, korzystając z [tego linku](https://www.ovh.com/manager/). Zostanie wyświetlony monit o zalogowanie się.

    ![Logowanie OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Na stronie docelowej pulpitu nawigacyjnego w obszarze **Wyświetl wszystkie moje działania** wybierz nazwę domeny, którą chcesz edytować.

1. Wybierz pozycję **Strefa DNS**.

    ![OVH Wybierz strefę DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. Wybierz **pozycję Dodaj wpis**.

    ![OVH Dodaj wpis.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. Wybierz pozycję **MX**.

    ![Typ rekordu OVH MX.](../../media/29b5e54e-440a-41f2-9eb9-3de573922ddf.png)

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z poniższej tabeli. Aby przypisać wartość czasu wygaśnięcia, wybierz pozycję **Niestandardowe** z listy rozwijanej, a następnie wpisz wartość w polu tekstowym.

    > [!NOTE]
    > Domyślnie OVH używa notacji względnej dla obiektu docelowego, co dodaje nazwę domeny na końcu rekordu docelowego. Aby zamiast tego użyć notacji bezwzględnej, dodaj kropkę do rekordu docelowego, jak pokazano w poniższej tabeli.

   |Domena podrzędna|Czas wygaśnięcia|Priority (Priorytet)|Target (Element docelowy)|
   |---|---|---|---|
   |(pozostaw puste)|3600 (sekundy)|0  <br/> Aby uzyskać więcej informacji o priorytetach, zobacz [Co to jest priorytet rekordu MX?](../setup/domains-faq.yml)|\<domain-key\>.mail.protection.outlook.com.  <br/> **Uwaga:** Pobierz dane *\<domain-key\>* z konta Microsoft. [Jak to znaleźć?](../get-help-with-domains/information-for-dns-records.md)|

    ![Rekord OVH MX dla poczty.](../../media/6e2f5655-93e2-4620-8f19-c452e7edf8f0.png)

1. Wybierz pozycję **Dalej**.

    ![Rekord OVH MX wybierz pozycję Dalej.](../../media/4db62d07-0dc4-49f6-bd19-2b4a07fd764a.png)

1. Wybierz pozycję **Potwierdź**.

    ![Rekord OVH MX wybierz pozycję Potwierdź.](../../media/090bfb11-a753-4af0-8982-582a4069a169.png)

1. Usuń wszystkie inne rekordy MX na liście na stronie **strefy DNS** . Wybierz każdy rekord i w kolumnie **Akcje** wybierz ikonę **kosza na śmieci Usuń** .

    ![OVH usuń rekord MX.](../../media/892b328b-7057-4828-b8c5-fe26284dc8c2.png)

1. Wybierz pozycję **Potwierdź**.

## <a name="add-the-cname-record-required-for-microsoft"></a>Dodawanie rekordu CNAME wymaganego dla firmy Microsoft

1. Aby rozpocząć, przejdź do strony domen w OVH, korzystając z [tego linku](https://www.ovh.com/manager/). Zostanie wyświetlony monit o zalogowanie się.

    ![Logowanie OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Na stronie docelowej pulpitu nawigacyjnego w obszarze **Wyświetl wszystkie moje działania** wybierz nazwę domeny, którą chcesz edytować.

1. Wybierz pozycję **Strefa DNS**.

    ![OVH Wybierz strefę DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. Wybierz **pozycję Dodaj wpis**.

    ![OVH Dodaj wpis.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. Wybierz pozycję **CNAME**.

    ![OVH Dodaj typ rekordu CNAME.](../../media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png)

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z pierwszego wiersza poniższej tabeli. Aby przypisać wartość czasu wygaśnięcia, wybierz pozycję **Niestandardowe** z listy rozwijanej, a następnie wpisz wartość w polu tekstowym.

   |Domena podrzędna|Czas wygaśnięcia|Target (Element docelowy)|
   |---|---|---|
   |autodiscover|3600 (sekundy)|autodiscover.outlook.com.|

    ![Rekord CNAME OVH.](../../media/516938b3-0b12-4736-a631-099e12e189f5.png)

1. Wybierz pozycję **Dalej**.

    ![OVH Dodaj wartości CNAME i wybierz przycisk Dalej.](../../media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png)

1. Wybierz pozycję **Potwierdź**.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Dodawanie rekordu TXT SPF w celu zapobiegania spamowi w wiadomościach e-mail

> [!IMPORTANT]
> Nie można mieć więcej niż jednego rekordu TXT na rekord SPF dla domeny. Jeśli domena ma więcej niż jeden rekord SPF, może to spowodować błędy poczty e-mail, a także problemy z dostarczaniem i klasyfikacją spamu. Jeśli masz już rekord SPF dla swojej domeny, nie twórz nowego rekordu dla firmy Microsoft. Zamiast tego dodaj wymagane wartości firmy Microsoft do bieżącego rekordu, aby mieć  *jeden*  rekord SPF zawierający oba zestawy wartości.

1. Aby rozpocząć, przejdź do strony domen w OVH, korzystając z [tego linku](https://www.ovh.com/manager/). Zostanie wyświetlony monit o zalogowanie się.

    ![Logowanie OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Na stronie docelowej pulpitu nawigacyjnego w obszarze **Wyświetl wszystkie moje działania** wybierz nazwę domeny, którą chcesz edytować.

1. Wybierz pozycję **Strefa DNS**.

    ![OVH Wybierz strefę DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. Wybierz **pozycję Dodaj wpis**.

    ![OVH Dodaj wpis.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. Wybierz pozycję **TXT**.

1. W polach nowego rekordu wpisz lub skopiuj i wklej następujące wartości. Aby przypisać wartość czasu wygaśnięcia, wybierz pozycję **Niestandardowe** z listy rozwijanej, a następnie wpisz wartość w polu tekstowym.

   |Domena podrzędna|Czas wygaśnięcia|Value|
   |---|---|---|
   |(pozostaw puste)|3600 (sekundy)|v=spf1 include:spf.protection.outlook.com -all <br/**Note:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostały poprawne.|

    ![OVH Dodaj rekord TXT dla SPF.](../../media/f50466e9-1557-4548-8a39-e98978a5ee2e.png)

1. Wybierz pozycję **Dalej**.

    ![OVH Dodaj rekord TXT dla SPF i wybierz przycisk Dalej.](../../media/7937eb7c-114f-479f-a916-bcbe476d6108.png)

1. Wybierz pozycję **Potwierdź**.

    ![OVH Dodaj rekord TXT dla SPF i Potwierdź.](../../media/649eefeb-3227-49e3-98a0-1ce19c42fa54.png)

## <a name="advanced-option-skype-for-business"></a>Opcja zaawansowana: Skype dla firm

Tę opcję należy wybrać tylko wtedy, gdy organizacja używa Skype dla firm dla usług komunikacji online, takich jak czat, połączenia konferencyjne i połączenia wideo, oprócz Microsoft Teams. Skype wymaga 4 rekordów: 2 rekordy SRV do komunikacji między użytkownikami i 2 rekordy CNAME, aby zalogować się i połączyć użytkowników z usługą.

### <a name="add-the-two-required-srv-records"></a>Dodawanie dwóch wymaganych rekordów SRV

1. Aby rozpocząć, przejdź do strony domen w OVH, korzystając z [tego linku](https://www.ovh.com/manager/). Zostanie wyświetlony monit o zalogowanie się.

    ![Logowanie OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Na stronie docelowej pulpitu nawigacyjnego w obszarze **Wyświetl wszystkie moje działania** wybierz nazwę domeny, którą chcesz edytować.

1. Wybierz pozycję **Strefa DNS**.

    ![OVH Wybierz strefę DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. Wybierz **pozycję Dodaj wpis**.

    ![OVH Dodaj wpis.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. Wybierz pozycję **SRV**.

1. W polach nowego rekordu wpisz lub skopiuj i wklej następujące wartości. Aby przypisać wartość czasu wygaśnięcia, wybierz pozycję **Niestandardowe** z listy rozwijanej, a następnie wpisz wartość w polu tekstowym.

   |Domena podrzędna|TTL (Seconds) [Czas wygaśnięcia (w sekundach)]|Priority (Priorytet)|Waga|Port|Target (Element docelowy)|
   |---|---|---|---|---|---|
   |_sip._tls|3600 (s.)|100|1|443|sipdir.online.lync.com. **Ta wartość MUSI kończyć się kropką (.)**><br> **Uwaga:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostały poprawne.|
   |_sipfederationtls._tcp|3600 (s.)|100|1|5061|sipfed.online.lync.com. **Wartość ta MUSI mieć na końcu kropkę (.)**<br> **Uwaga:** Zalecamy skopiowanie i wklejenie tego wpisu, aby wszystkie odstępy pozostały poprawne.|

1. Aby dodać inny rekord SRV, wybierz pozycję **Dodaj kolejny rekord**, utwórz rekord przy użyciu wartości z następnego wiersza w tabeli, a następnie wybierz pozycję **Utwórz rekordy**.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli masz problemy z przepływem poczty lub inne problemy po dodaniu rekordów DNS, zobacz [Znajdowanie i rozwiązywanie problemów po dodaniu domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Dodaj dwa wymagane rekordy CNAME dla Skype dla firm

1. Aby rozpocząć, przejdź do strony domen w OVH, korzystając z [tego linku](https://www.ovh.com/manager/). Zostanie wyświetlony monit o zalogowanie się.

    ![Logowanie OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Na stronie docelowej pulpitu nawigacyjnego w obszarze **Wyświetl wszystkie moje działania** wybierz nazwę domeny, którą chcesz edytować.

1. Wybierz pozycję **Strefa DNS**.

    ![OVH Wybierz strefę DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. Wybierz **pozycję Dodaj wpis**.

    ![OVH Dodaj wpis.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. Wybierz pozycję **CNAME**.

    ![OVH Dodaj typ rekordu CNAME.](../../media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png)

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z pierwszego wiersza poniższej tabeli. Aby przypisać wartość czasu wygaśnięcia, wybierz pozycję **Niestandardowe** z listy rozwijanej, a następnie wpisz wartość w polu tekstowym.

   |Domena podrzędna|Czas wygaśnięcia|Target (Element docelowy)|
   |---|---|---|
   |sip|3600 (s.)|sipdir.online.lync.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)**|
   |lyncdiscover|3600 (s.)|webdir.online.lync.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)**|

1. Wybierz pozycję **Dalej**.

    ![OVH Dodaj wartości CNAME i wybierz przycisk Dalej.](../../media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png)

1. Wybierz pozycję **Potwierdź**.

1. Dodaj inny rekord CNAME.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Opcja zaawansowana: Intune i mobile Zarządzanie urządzeniami dla Microsoft 365

Ta usługa ułatwia zabezpieczanie i zdalne zarządzanie urządzeniami przenośnymi łączącymi się z domeną. Usługa Mobile Zarządzanie urządzeniami wymaga dwóch rekordów CNAME, aby użytkownicy mogli rejestrować urządzenia w usłudze.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Dodaj dwa wymagane rekordy CNAME dla usługi Mobile Zarządzanie urządzeniami

1. Aby rozpocząć, przejdź do strony domen w OVH, korzystając z [tego linku](https://www.ovh.com/manager/). Zostanie wyświetlony monit o zalogowanie się.

    ![Logowanie OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Na stronie docelowej pulpitu nawigacyjnego w obszarze **Wyświetl wszystkie moje działania** wybierz nazwę domeny, którą chcesz edytować.

1. Wybierz pozycję **Strefa DNS**.

    ![OVH Wybierz strefę DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. Wybierz **pozycję Dodaj wpis**.

    ![OVH Dodaj wpis.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. Wybierz pozycję **CNAME**.

    ![OVH Dodaj typ rekordu CNAME.](../../media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png)

1. W polach nowego rekordu wpisz lub skopiuj i wklej wartości z pierwszego wiersza poniższej tabeli. Aby przypisać wartość czasu wygaśnięcia, wybierz pozycję **Niestandardowe** z listy rozwijanej, a następnie wpisz wartość w polu tekstowym.

   |Domena podrzędna|Czas wygaśnięcia|Target (Element docelowy)|
   |---|---|---|
   |enterpriseregistration  <br/>|3600 (s.)|enterpriseregistration.windows.net.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)**|
   |enterpriseenrollment|3600 (s.)|enterpriseenrollment-s.manage.microsoft.com.  <br/> **Wartość ta MUSI mieć na końcu kropkę (.)**|

1. Wybierz pozycję **Dalej**.

    ![OVH Dodaj wartości CNAME i wybierz przycisk Dalej.](../../media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png)

1. Wybierz pozycję **Potwierdź**.

1. Dodaj inny rekord CNAME.

> [!NOTE]
> Wprowadzenie zmian w systemie DNS trwa zwykle około 15 minut. Jednak czasem aktualizacja internetowego systemu DNS może potrwać dłużej. Jeśli po dodaniu rekordów DNS występują problemy z przepływem poczty e-mail lub inne, zobacz [Rozwiązywanie problemów po zmianie nazwy domeny lub rekordów DNS](../get-help-with-domains/find-and-fix-issues.md).