---
title: Dodawanie rekordów DNS w celu połączenia domeny
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
search.appverid:
- MET150
description: Połączenie domeny u dowolnego dostawcy hostingu DNS, aby Microsoft 365, weryfikując domenę i aktualizując rekordy DNS na koncie rejestratora.
ms.custom:
- okr_smb
- AdminSurgePortfolio
- AdminTemplateSet
- business_assist
- admindeeplinkMAC
ms.openlocfilehash: 17a3a63dfb3faedb5ff213b24dd14abd57f55bb3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63316929"
---
# <a name="add-dns-records-to-connect-your-domain"></a>Dodawanie rekordów DNS w celu połączenia domeny

Jeśli domenę kupiono od zewnętrznego dostawcy hostingu, możesz połączyć ją z usługą Microsoft 365 aktualizując rekordy DNS na koncie rejestratora.

Po zakończeniu tych kroków Twoja domena pozostanie zarejestrowana u hosta, u który zakupiono domenę, ale Microsoft 365 może używać jej do adresów e-mail (takich jak user@yourdomain.com) i innych usług.

Jeśli nie dodasz domeny, osoby w Twojej organizacji będą używać domeny adresowej onmicrosoft.com swoich adresów e-mail, dopóki nie to zrobisz. Ważne jest dodanie domeny przed dodaniem użytkowników, aby nie trzeba było ich dwukrotnie  skonfigurować.

[Zajrzyj do często zadawanych](../setup/domains-faq.yml) pytań domeny, jeśli nie możesz znaleźć szukanych informacji poniżej.

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczącej czynności opisanej w tym temacie, rozważ współpracę z specjalistą [ds. małej firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej Ty i Twoi pracownicy możecie uzyskać całodobowy dostęp do małych ekspertów biznesowych, gdy rozwijasz swoją firmę, od dołączania do codziennego użytku.

## <a name="step-1-add-a-txt-or-mx-record-to-verify-you-own-the-domain"></a>Krok 1. Dodawanie rekordu TXT lub MX w celu zweryfikowania, że jest się właścicielem domeny

### <a name="recommended-verify-with-a-txt-record"></a>Zalecane: weryfikowanie za pomocą rekordu TXT

Najpierw musisz udowodnić, że jesteś właścicielem domeny, którą chcesz dodać do Microsoft 365.

1. Zaloguj się do centrum administracyjne platformy Microsoft 365 i **wybierz pozycję Pokaż wszystkie** >  **Ustawienia** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domains**</a>.
2. W nowej karcie lub oknie przeglądarki zaloguj się do swojego dostawcy hostingu DNS, a następnie znajdź miejsce, w którym zarządzasz swoimi ustawieniami DNS (np. Zone File Ustawienia, Manage Domains, Domain Manager, DNS Manager).
3. Przejdź do strony Menedżera DNS swojego dostawcy i dodaj rekord TXT wskazany w centrum administracyjnym do swojej domeny.

   Dodanie tego rekordu nie ma wpływu na istniejące wiadomości e-mail ani inne usługi i możesz go bezpiecznie usunąć po nadaniu domenie połączenia z usługą Microsoft 365.

   Przykład:

   - TXT Name (Nazwa TXT): `@`
   - TXT Value (Wartość TXT): MS=ms######## (unikatowy identyfikator w centrum administracyjnym)
   - TTL `3600` (Czas wygaśnięcia): (lub domyślny dostawca)

4. Zapisz rekord, wróć do centrum administracyjnego, a następnie wybierz pozycję **Weryfikuj**. Zarejestrowanie zmian w rekordzie trwa zwykle około 15 minut, ale czasami może potrwać dłużej. Może upłynie trochę czasu, a kilka osób spróbuje pochylić się nad zmianą.

Gdy firma Microsoft znajdzie właściwy rekord TXT, domena zostanie zweryfikowana.

### <a name="verify-with-an-mx-record"></a>Weryfikowanie za pomocą rekordu MX

Jeśli rejestrator nie obsługuje dodawania rekordów TXT, możesz to sprawdzić, dodając rekord MX.

1. Zaloguj się do centrum administracyjne platformy Microsoft 365 i **wybierz pozycję Pokaż wszystkie** >  **Ustawienia** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domains**</a>.
2. W nowej karcie lub oknie przeglądarki zaloguj się do swojego dostawcy hostingu DNS, a następnie znajdź miejsce, w którym zarządzasz swoimi ustawieniami DNS (np. Zone File Ustawienia, Manage Domains, Domain Manager, DNS Manager).
3. Przejdź do strony Menedżera DNS swojego dostawcy i dodaj rekord MX wskazany w centrum administracyjnym do swojej domeny.

Priorytet tego rekordu MX **musi** być najwyższy ze wszystkich istniejących rekordów MX dla domeny. W przeciwnym razie może to zakłócać wysyłanie i odbieranie wiadomości e-mail. Te rekordy należy usunąć zaraz po zakończeniu weryfikacji domeny.

Upewnij się, że w polach są ustawione następujące wartości:

- Typ rekordu: `MX`
- Priorytet: ustaw dowolną dużą wartość, która jeszcze nie jest używana.
- Nazwa hosta: `@`
- Points to address (Wskazuje adres): skopiuj wartość z centrum administracyjnego i wklej ją w tym miejscu.
- TTL `3600` (Czas wygaśnięcia): (lub domyślny dostawca)

Gdy firma Microsoft znajdzie właściwy rekord MX, domena zostanie zweryfikowana.

## <a name="step-2-add-dns-records-to-connect-microsoft-services"></a>Krok 2. Dodawanie rekordów DNS w celu nawiązania połączenia usługi firmy Microsoft

Na nowej karcie lub w nowym oknie przeglądarki zaloguj się do swojego dostawcy hostingu DNS i znajdź miejsce, w którym zarządzasz swoimi ustawieniami DNS (np. Zone File Ustawienia, Manage Domains, Domain Manager, DNS Manager).

Dodajemy kilka różnych typów rekordów DNS w zależności od usług, które chcesz włączyć.

### <a name="add-an-mx-record-for-email-outlook-exchange-online"></a>Dodawanie rekordu MX dla poczty e-mail (Outlook, Exchange Online)

**Przed rozpoczęciem:** Jeśli użytkownicy mają już adresy e-mail z Twoją domeną (na przykład user@yourdomain.com), utwórz ich konta w centrum administracyjnym przed skonfigurowaniem rekordów MX. Dzięki temu będą oni nadal otrzymywać wiadomości e-mail. Po zaktualizowaniu rekordu MX domeny wszystkie nowe wiadomości e-mail dla wszystkich osób korzystających z Twojej domeny będą trafiać do Microsoft 365. Wszystkie już posiadane wiadomości e-mail pozostają u bieżącego hosta poczty e-mail, chyba że zdecydujesz się na migrowanie wiadomości e-mail i [kontaktów do Microsoft 365.](../setup/migrate-email-and-contacts-admin.md)

Informacje dotyczące rekordu MX można uzyskać z kreatora konfiguracji domeny w centrum administracyjnym.

W witrynie internetowej dostawcy hostingu dodaj nowy rekord MX.
Upewnij się, że w polach są ustawione następujące wartości:

- Typ rekordu: `MX`
- Priority (Priorytet): ustawiana na najwyższą dostępną wartość, zazwyczaj `0`.
- Nazwa hosta: `@`
- Points to address (Wskazuje adres): skopiuj wartość z centrum administracyjnego i wklej ją w tym miejscu.
- TTL `3600` (Czas wygaśnięcia): (lub domyślny dostawca)

Zapisz rekord, a następnie usuń wszelkie inne rekordy MX.

### <a name="add-cname-records-to-connect-other-services-teams-exchange-online-aad-mdm"></a>Dodawanie rekordów CNAME w celu połączenia innych usług (Teams, Exchange Online, AAD, MDM)

Informacje dotyczące rekordów CNAME można uzyskać z kreatora konfiguracji domeny w centrum administracyjnym.

W witrynie internetowej dostawcy hostingu dodaj rekordy CNAME dla każdej usługi, którą chcesz połączyć.
Upewnij się, że w polach są ustawione następujące wartości dla każdego z nich:

- Typ rekordu: `CNAME (Alias)`
- Host: wklej tutaj wartości skopiowane z centrum administracyjnego.
- Points to address (Wskazuje adres): skopiuj wartość z centrum administracyjnego i wklej ją w tym miejscu.
- TTL `3600` (Czas wygaśnięcia): (lub domyślny dostawca)

### <a name="add-or-edit-an-spf-txt-record-to-help-prevent-email-spam-outlook-exchange-online"></a>Dodawanie lub edytowanie rekordu TXT SPF w celu zapobiegania spamowi w wiadomościach e-mail (Outlook, Exchange Online)

**Przed rozpoczęciem:** Jeśli masz już rekord SPF dla swojej domeny, nie twórz nowego rekordu dla Microsoft 365. Zamiast tego dodaj wymagane wartości Microsoft 365 do bieżącego rekordu w witrynie sieci Web dostawców hostingu, aby mieć pojedynczy *rekord SPF,* który zawiera oba zestawy wartości.

W witrynie internetowej dostawcy hostingu edytuj istniejący rekord SPF lub utwórz rekord SPF.
Upewnij się, że w polach są ustawione następujące wartości:

- Typ rekordu: `TXT (Text)`
- Host: `@`
- TXT Value (Wartość TXT): `v=spf1 include:spf.protection.outlook.com -all`
- TTL `3600` (Czas wygaśnięcia): (lub domyślny dostawca)

Zapisz rekord.

Weryfikowanie rekordu SPF przy użyciu jednego z tych [narzędzi do weryfikowania rekordu SPF](/office365/admin/setup/domains-faq#how-can-i-validate-spf-records-for-my-domain)

Spf został zaprojektowany w celu zapobiegania fałszerszem, ale istnieją techniki podszywania się, przed które spf nie chroni. Aby zapewnić ochronę przed tymi ustawieniami, po skonfigurowaniu spf musisz również skonfigurować ustawienia DKIM i DMARC dla Microsoft 365.

Aby rozpocząć, zobacz Używanie funkcji [DKIM](../../security/office-365-security/use-dkim-to-validate-outbound-email.md) w celu weryfikacji wychodzących wiadomości e-mail wysłanych z domeny w programie Microsoft 365 i Używanie funkcji [DMARC](../../security/office-365-security/use-dmarc-to-validate-email.md) do sprawdzania poprawności wiadomości e-mail w Microsoft 365.

### <a name="add-srv-records-for-communications-services-teams-skype-for-business"></a>Dodawanie rekordów SRV do usług telekomunikacyjnych (Teams, Skype dla firm)

W witrynie internetowej dostawcy hostingu dodaj rekordy SRV dla każdej usługi, którą chcesz połączyć.
Upewnij się, że w polach są ustawione następujące wartości dla każdego z nich:

- Typ rekordu: `SRV (Service)`
- Nazwa: `@`
- Target (Wartość docelowa): skopiuj wartość z centrum administracyjnego i wklej ją tutaj.
- Protocol (Protokół): skopiuj wartość z centrum administracyjnego i wklej ją w tym miejscu.
- Usługa: skopiuj wartość z centrum administracyjnego i wklej ją w tym miejscu.
- Priorytet: `100`
- Waga: `1`
- Port: skopiuj wartość z centrum administracyjnego i wklej ją tutaj.
- TTL `3600` (Czas wygaśnięcia): (lub domyślny dostawca)

Zapisz rekord.

#### <a name="srv-record-field-restrictions-and-workarounds"></a>Ograniczenia i obejścia dotyczące pól rekordów SRV

Niektórzy dostawcy hostingu nałożyli ograniczenia na wartości pól w rekordach SRV. Oto niektóre typowe obejścia tych ograniczeń.

##### <a name="name"></a>Name (Nazwa)

Jeśli dostawca hostingu nie zezwala na ustawienie dla tego pola wartości **@**, pozostaw to pole puste. Tej metody należy *używać tylko* wtedy, gdy dostawca hostingu ma oddzielne pola dla wartości Service (Usługa) i Protocol (Protokół). W przeciwnym razie zapoznaj się z poniższymi uwagami na temat protokołów Service (Usługa) i Protocol (Protokół).

##### <a name="service-and-protocol"></a>Service and Protocol

Jeśli Twój dostawca hostingu nie udostępni tych pól dla rekordów SRV, musisz określić wartości **Service** (Usługa) i **Protocol** (Protokół) w polu **Name (Nazwa) rekordu** . Uwaga: W zależności od dostawcy hostingu pole **Name** (Nazwa) może mieć inne nazwę, na przykład: **Host**, **Hostname** (Nazwa hosta) lub **Subdomain (Poddomena**). Aby dodać te wartości, należy utworzyć jeden ciąg, oddzielając wartości kropką.

Przykład: `_sip._tls`

##### <a name="priority-weight-and-port"></a>Priority (Priorytet), Weight (Waga) i Port (Port)

Jeśli Twój dostawca hostingu nie udostępni tych pól na przykład dla rekordów SRV, musisz je określić w polu **Target (Element docelowy) rekordu** . Uwaga: W zależności od dostawcy hostingu pole **Target** (Element docelowy) może mieć inne nazwę, na przykład: **Content** (Zawartość), **IP Address** (Adres IP) lub **Target Host (Host docelowy**).

Aby dodać te wartości, utwórz jeden ciąg, oddzielając wartości spacjami i czasami kończąc się kropką *(w* razie wątpliwości skontaktuj się z dostawcą). Wartości muszą być uwzględnione w tej kolejności: Priority (Priorytet), Weight (Waga), Port, Target (Element docelowy).

- Przykład 1. `100 1 443 sipdir.online.lync.com.`
- Przykład 2. `100 1 443 sipdir.online.lync.com`

## <a name="related-content"></a>Zawartość pokrewna

[Zmienianie serwerów nazw w celu skonfigurowania Microsoft 365 rejestratora](change-nameservers-at-any-domain-registrar.md) domen (artykuł)\
[Znajdowanie i rozwiązywanie problemów po dodaniu domeny lub rekordów DNS](find-and-fix-issues.md) (artykuł)\
[Zarządzanie domenami](/admin) (strona linku)
