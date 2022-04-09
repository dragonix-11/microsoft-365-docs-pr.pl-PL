---
title: Dodaj rekordy DNS, aby połączyć domenę
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
description: Połącz domenę u dowolnego dostawcy hostingu DNS z platformą Microsoft 365, weryfikując domenę i aktualizując rekordy DNS na koncie rejestratora.
ms.custom:
- okr_smb
- AdminSurgePortfolio
- AdminTemplateSet
- business_assist
- admindeeplinkMAC
ms.openlocfilehash: 08d28a5586c92d0e439170807f750150d9fbe17c
ms.sourcegitcommit: 5c9137f98e688ab23c144e75687399e390bb2601
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2022
ms.locfileid: "64704784"
---
# <a name="add-dns-records-to-connect-your-domain"></a>Dodaj rekordy DNS, aby połączyć domenę

Jeśli domenę kupiono od zewnętrznego dostawcy hostingu, możesz połączyć ją z platformą Microsoft 365, aktualizując rekordy DNS na koncie rejestratora.

Po zakończeniu tych kroków Twoja domena pozostanie zarejestrowana u hosta, u którego zakupiono domenę, ale platforma Microsoft 365 może używać jej do adresów e-mail (takich jak user@yourdomain.com) i innych usług.

Jeśli nie dodasz domeny, osoby w Twojej organizacji będą używać domeny onmicrosoft.com jako swoich adresów e-mail, dopóki tego nie zrobisz. Ważne jest dodanie domeny przed dodaniem użytkowników, aby nie trzeba było ich dwukrotnie skonfigurować.

[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml), jeśli nie możesz znaleźć szukanych informacji poniżej.

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczących kroków opisanych w tym temacie, rozważ [współpracę ze specjalistą ds. małej firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej Ty i Twoi pracownicy możecie uzyskać całodobowy dostęp do specjalistów ds. małej firmy, gdy rozwijasz swoją firmę, od momentu dołączenia po codzienne użytkowanie.

## <a name="step-1-add-a-txt-or-mx-record-to-verify-you-own-the-domain"></a>Krok 1: Dodawanie rekordu TXT lub MX w celu zweryfikowania, że jest się właścicielem domeny

### <a name="recommended-verify-with-a-txt-record"></a>Zalecane: weryfikowanie za pomocą rekordu TXT

Najpierw musisz udowodnić, że jesteś właścicielem domeny, którą chcesz dodać do platformy Microsoft 365.

1. Zaloguj się do centrum administracyjnego platformy Microsoft 365 i wybierz pozycję **Pokaż wszystkie** > **Ustawienia** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domeny**</a>.
2. W nowej karcie lub oknie przeglądarki zaloguj się do dostawcy hostingu DNS, a następnie znajdź lokalizację zarządzania ustawieniami DNS (np. Ustawienia pliku strefy, Zarządzanie domenami, Menedżer domeny, Menedżer DNS).
3. Przejdź do strony Menedżera DNS swojego dostawcy i dodaj rekord TXT wskazany w centrum administracyjnym do swojej domeny.

   Dodanie tego rekordu nie ma wpływu na istniejącą pocztę e-mail ani inne usługi i możesz go bezpiecznie usunąć po nadaniu domenie połączenia z platformą Microsoft 365.

   Przykład:

   - Nazwa TXT: `@`
   - Wartość TXT: MS=ms######## (unikatowy identyfikator z centrum administracyjnego)
   - TTL `3600` (Czas wygaśnięcia): (lub domyślny dostawca)

4. Zapisz rekord, wróć do centrum administracyjnego, a następnie wybierz pozycję **Weryfikuj**. Zarejestrowanie zmian w rekordzie trwa zwykle około 15 minut, ale czasami może potrwać dłużej. Daj mu trochę czasu i pozwól na kilka prób, aby wychwycił zmianę.

Gdy firma Microsoft znajdzie właściwy rekord TXT, domena zostanie zweryfikowana.

### <a name="verify-with-an-mx-record"></a>Weryfikowanie za pomocą rekordu MX

Jeśli rejestrator nie obsługuje dodawania rekordów TXT, możesz to sprawdzić, dodając rekord MX.

1. Zaloguj się do centrum administracyjnego platformy Microsoft 365 i wybierz pozycję **Pokaż wszystkie** > **Ustawienia** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domeny**</a>.
2. W nowej karcie lub oknie przeglądarki zaloguj się do dostawcy hostingu DNS, a następnie znajdź lokalizację zarządzania ustawieniami DNS (np. Ustawienia pliku strefy, Zarządzanie domenami, Menedżer domeny, Menedżer DNS).
3. Przejdź do strony Menedżera DNS swojego dostawcy i dodaj rekord MX wskazany w centrum administracyjnym do swojej domeny.

**Priority** (Priorytet) tego rekordu MX musi być najwyższy ze wszystkich istniejących rekordów MX dla domeny. W przeciwnym razie może to zakłócać wysyłanie i odbieranie wiadomości e-mail. Te rekordy należy usunąć zaraz po zakończeniu weryfikacji domeny.

Upewnij się, że pola są ustawione na następujące wartości:

- Typ rekordu: `MX`
- Priority (Priorytet): ustaw dowolną dużą wartość, która jeszcze nie jest używana.
- Nazwa hosta: `@`
- Punkty do zaadresowania: skopiuj wartość z centrum administracyjnego i wklej ją w tym miejscu.
- TTL `3600` (Czas wygaśnięcia): (lub domyślny dostawca)

Gdy firma Microsoft znajdzie właściwy rekord MX, domena zostanie zweryfikowana.

## <a name="step-2-add-dns-records-to-connect-microsoft-services"></a>Krok 2. Dodawanie rekordów DNS, aby połączyć usługi firmy Microsoft

Na nowej karcie lub w nowym oknie przeglądarki zaloguj się do swojego dostawcy hostingu DNS i znajdź lokalizację zarządzania ustawieniami DNS (np. Ustawienia pliku strefy, Zarządzanie domenami, Menedżer domeny, Menedżer DNS)

W zależności od usług, które chcesz włączyć, będziesz dodawać kilka różnych typów rekordów DNS.

### <a name="add-an-mx-record-for-email-outlook-exchange-online"></a>Dodawanie rekordu MX dla poczty e-mail (Outlook, Exchange Online)

**Przed rozpoczęciem:** Jeśli użytkownicy mają już adresy e-mail z Twoją domeną (na przykład user@yourdomain.com), utwórz ich konta w centrum administracyjnym przed skonfigurowaniem rekordów MX. Dzięki temu będą oni nadal otrzymywać wiadomości e-mail. Po zaktualizowaniu rekordu MX domeny wszystkie nowe wiadomości e-mail dla wszystkich osób korzystających z Twojej domeny będą trafiać na platformę Microsoft 365. Wszystkie już posiadane wiadomości e-mail pozostają u bieżącego hosta poczty e-mail, chyba że zdecydujesz się na [migrowanie wiadomości e-mail i kontaktów do platformy Microsoft 365.](../setup/migrate-email-and-contacts-admin.md)

Informacje dotyczące rekordu MX można uzyskać z kreatora konfiguracji domeny w centrum administracyjnym.

W witrynie internetowej dostawcy hostingu dodaj nowy rekord MX. Upewnij się, że pola są ustawione na następujące wartości:

- Typ rekordu: `MX`
- Priority (Priorytet): ustawianie na najwyższą dostępną wartość, zazwyczaj `0`.
- Nazwa hosta: `@`
- Punkty do zaadresowania: skopiuj wartość z centrum administracyjnego i wklej ją w tym miejscu.
- TTL: `3600`

> [!NOTE]
> Usługa Exchange Online obsługuje tylko wartości czasu wygaśnięcia krótsze niż 6 godzin (21 600 sekund).

Zapisz rekord, a następnie usuń wszelkie inne rekordy MX.

### <a name="add-cname-records-to-connect-other-services-teams-exchange-online-aad-mdm"></a>Dodawanie rekordów CNAME w celu połączenia innych usług (Teams, Exchange Online, AAD, MDM)

Informacje dotyczące rekordów CNAME można uzyskać z kreatora konfiguracji domeny w centrum administracyjnym.

W witrynie internetowej dostawcy hostingu dodaj rekordy CNAME dla każdej usługi, którą chcesz połączyć.
Upewnij się, że pola są ustawione następujące wartości dla każdego z nich:

- Typ rekordu: `CNAME (Alias)`
- Host: wklej tutaj wartości skopiowane z centrum administracyjnego.
- Punkty do zaadresowania: skopiuj wartość z centrum administracyjnego i wklej ją w tym miejscu.
- TTL `3600` (Czas wygaśnięcia): (lub domyślny dostawca)

### <a name="add-or-edit-an-spf-txt-record-to-help-prevent-email-spam-outlook-exchange-online"></a>Dodawanie lub edytowanie rekordu TXT SPF w celu zapobiegania spamowi w wiadomościach e-mail (Outlook, Exchange Online)

**Zanim zaczniesz:** Jeśli masz już rekord SPF dla swojej domeny, nie twórz nowego rekordu dla platformy Microsoft 365. Zamiast tego dodaj wymagane wartości platformy Microsoft 365 do bieżącego rekordu w witrynie internetowej dostawcy hostingu, aby mieć *pojedynczy* rekord SPF zawierający oba zestawy wartości.

W witrynie internetowej dostawcy hostingu edytuj istniejący rekord SPF lub utwórz rekord SPF.
Upewnij się, że pola są ustawione na następujące wartości:

- Typ rekordu: `TXT (Text)`
- Host: `@`
- Wartość TXT: `v=spf1 include:spf.protection.outlook.com -all`
- TTL `3600` (Czas wygaśnięcia): (lub domyślny dostawca)

Zapisz rekord.

Weryfikowanie rekordu SPF przy użyciu jednego z tych [narzędzi do weryfikowania rekordu SPF](/office365/admin/setup/domains-faq#how-can-i-validate-spf-records-for-my-domain)

Mechanizm SPF ułatwia zapobieganie podszywaniu się, ale istnieją techniki podszywania się, przed którymi mechanizm SPF nie chroni. Aby zapewnić ochronę przed tego rodzaju technikami, po skonfigurowaniu mechanizmu SPF musisz również skonfigurować funkcje DKIM i DMARC dla platformy Microsoft 365.

Aby rozpocząć, zobacz [Używanie funkcji DKIM w celu weryfikacji wychodzących wiadomości e-mail wysłanych z domeny na platformie Microsoft 365](../../security/office-365-security/use-dkim-to-validate-outbound-email.md) i [Używanie funkcji DMARC do weryfikacji wiadomości e-mail na platformie Microsoft 365](../../security/office-365-security/use-dmarc-to-validate-email.md).

### <a name="add-srv-records-for-communications-services-teams-skype-for-business"></a>Dodawanie rekordów SRV do usług komunikacyjnych (Teams, Skype dla firm)

W witrynie internetowej dostawcy hostingu dodaj rekordy SRV dla każdej usługi, którą chcesz połączyć.
Upewnij się, że pola są ustawione następujące wartości dla każdego z nich:

- Typ rekordu: `SRV (Service)`
- Nazwa: `@`
- Target (Element docelowy): skopiuj wartość z centrum administracyjnego i wklej ją tutaj.
- Protokół: skopiuj wartość z centrum administracyjnego i wklej ją w tym miejscu.
- Usługa: skopiuj wartość z centrum administracyjnego i wklej ją w tym miejscu.
- Priority (Priorytet): `100`
- Weight (Waga): `1`
- Port: skopiuj wartość z centrum administracyjnego i wklej ją tutaj.
- TTL `3600` (Czas wygaśnięcia): (lub domyślny dostawca)

Zapisz rekord.

#### <a name="srv-record-field-restrictions-and-workarounds"></a>Ograniczenia i obejścia dotyczące pól rekordów SRV

Niektórzy dostawcy hostingu nałożyli ograniczenia na wartości pól w rekordach SRV. Poniżej przedstawiono kilka typowych obejść tych ograniczeń.

##### <a name="name"></a>Name (Nazwa)

Jeśli dostawca hostingu nie zezwala na ustawienie tego pola na **@**, pozostaw to pole puste. Tej metody należy używać *tylko* wtedy, gdy dostawca hostingu ma oddzielne pola dla wartości Service (Usługa) i Protocol (Protokół). W przeciwnym razie zapoznaj się z poniższymi uwagami dotyczącymi pól Service (Usługa) i Protocol (Protokół).

##### <a name="service-and-protocol"></a>Service (Usługa) i Protocol (Protokół)

Jeśli Twój dostawca hostingu nie udostępni tych pól dla rekordów SRV, musisz określić wartości **Service** (Usługa) i **Protocol** (Protokół) w polu **Name** (Nazwa) rekordu. (Uwaga: W zależności od dostawcy hostingu pole **Name** (Nazwa) może mieć inne nazwę, na przykład: **Host**, **Hostname** (Nazwa hosta) lub **Subdomain** (Poddomena)). Aby dodać te wartości, należy utworzyć jeden ciąg, oddzielając wartości kropką.

Przykład: `_sip._tls`

##### <a name="priority-weight-and-port"></a>Priority (Priorytet), Weight (Waga) i Port

Jeśli Twój dostawca hostingu nie udostępni tych pól dla rekordów SRV, musisz je określić w polu **Target** (Element docelowy) rekordu. (Uwaga: W zależności od dostawcy hostingu pole **Target** (Element docelowy) może mieć inne nazwę, na przykład: **Content** (Zawartość), **IP Address** (Adres IP) lub **Target Host** (Host docelowy)).

Aby dodać te wartości, utwórz jeden ciąg, oddzielając wartości spacjami i *czasami kończąc kropką* (skontaktuj się z dostawcą, jeśli nie masz pewności). Wartości muszą być uwzględnione w następującej kolejności: Priorytet, Waga, Port, Cel.

- Przykład 1: `100 1 443 sipdir.online.lync.com.`
- Przykład 2: `100 1 443 sipdir.online.lync.com`

## <a name="related-content"></a>Zawartość pokrewna

[Zmienianie serwerów nazw w celu skonfigurowania platformy Microsoft 365 u dowolnego rejestratora domen](change-nameservers-at-any-domain-registrar.md) (artykuł)\
[Znajdowanie i rozwiązywanie problemów po dodaniu swojej domeny lub rekordów DNS](find-and-fix-issues.md) (artykuł)\
[Zarządzanie domenami](/admin) (strona linku)
