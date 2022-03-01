---
title: Zwiększanie ochrony przed zagrożeniami w Microsoft 365 dla firm
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
- adminvideo
search.appverid:
- BCS160
- MET150
description: Skonfiguruj usługę Microsoft Defender na Office 365 ochrony poufnych danych przed wyłudzaniem informacji, złośliwym oprogramowaniem i innymi zagrożeniami.
ms.openlocfilehash: 8bf954930edc94ccf750bb334a62a4c8a4581f80
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/02/2022
ms.locfileid: "63009821"
---
# <a name="increase-threat-protection"></a>Zwiększanie ochrony przed zagrożeniami

Ten artykuł ułatwia zwiększenie ochrony subskrypcji usługi Microsoft 365 w celu ochrony przed wyłudzaniem informacji, złośliwym oprogramowaniem i innymi zagrożeniami. Te zalecenia są odpowiednie dla organizacji ze zwiększoną potrzebą zabezpieczeń, takich jak biura prawne i pracowników opieki zdrowotnej.

Przed rozpoczęciem należy sprawdzić wynik Office 365 bezpiecznej. Office 365 bezpiecznego wyniku analizuje zabezpieczenia organizacji na podstawie zwykłych działań i ustawień zabezpieczeń, a następnie przypisuje wynik. Zacznij od notacji bieżącego wyniku. Aby zwiększyć wynik, wykonaj czynności zalecane w tym artykule. Celem nie jest osiągnięcie maksymalnej liczby wyników, ale świadomość możliwości ochrony środowiska, które nie mają negatywnego wpływu na wydajność pracy użytkowników.

Aby uzyskać więcej informacji, zobacz [Microsoft Secure Score](../../security/defender/microsoft-secure-score.md).

## <a name="raise-the-level-of-protection-against-malware-in-mail"></a>Podnoszenie poziomu ochrony przed złośliwym oprogramowaniem w wiadomościach e-mail

Środowisko Office 365 lub Microsoft 365 obejmuje ochronę przed złośliwym oprogramowaniem. Możesz zwiększyć tę ochronę, blokując załączniki za pomocą typów plików, które są często używane w przypadku złośliwego oprogramowania. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OA7Z?autoplay=false]

1. Z centrum <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjne platformy Microsoft 365</a> pozycję Pokaż **więcej**, **Centra administracyjne**, a następnie **Pozycję Zabezpieczenia**.

1. Przejdź do **zasad & e-mail i** \> **zasad & zasad zagrożeń**\>.

1. Spośród dostępnych zasad wybierz pozycję **Ochrona przed złośliwym oprogramowaniem**.

Aby zwiększyć ochronę przed złośliwym oprogramowaniem w wiadomościach e-mail:

1. W portalu <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender przejdź</a> \> do sekcji Zasady & **e-mail** **i & zasady** \>  \> zagrożeń chroniące przed złośliwym oprogramowaniem w **sekcji** Zasady.

2. Na stronie **ochrony przed złośliwym oprogramowaniem** kliknij dwukrotnie pozycję **Domyślne (domyślne**). Zostanie wyświetlone wysuw. 

3. Wybierz **pozycję Edytuj ustawienia ochrony** u dołu wysuwu. 

4. w **obszarze Ustawienia** ochrony zaznacz pole wyboru obok opcji **Włącz filtr typowych załączników**. Blokowane typy plików są wymienione bezpośrednio pod kontrolką. Upewnij się, że dodano następujące typy plików:

   `ade, adp, ani, bas, bat, chm, cmd, com, cpl, crt, hlp, ht, hta, inf, ins, isp, job, js, jse, lnk, mda, mdb, mde, mdz, msc, msi, msp, mst, pcd, reg, scr, sct, shs, url, vb, vbe, vbs, wsc, wsf, wsh, exe, pif`

   Aby dodać lub usunąć typy plików, wybierz pozycję Dostosuj **typy** plików na końcu listy.

6. Wybierz **pozycję Zapisz.**

Aby uzyskać więcej informacji, zobacz [Ochrona przed złośliwym oprogramowaniem w uchcie EOP](../../security/office-365-security/anti-malware-protection.md).

## <a name="protect-against-ransomware"></a>Ochrona przed oprogramowaniem wymuszającym okup

Oprogramowanie wymuszające okup ogranicza dostęp do danych przez szyfrowanie plików lub blokowanie ekranów komputera. Następnie próbuje wyłudzić pieniądze od osób, które szły na kartce, prosząc o "ransom" zwykle w formie banków, takich jak Waluty, w zamian za dostęp do danych.

Aby chronić przed oprogramowaniem wymuszającym okup, utwórz co najmniej jedną regułę przepływu poczty, aby blokować rozszerzenia plików, które są często używane dla oprogramowania wymuszającego okup. (Te reguły zostały dodane w kroku [podnieść poziom ochrony przed](#raise-the-level-of-protection-against-malware-in-mail) złośliwym oprogramowaniem). Możesz również ostrzegać użytkowników, którzy otrzymają te załączniki w wiadomościach e-mail.

Oprócz plików zablokowanych w poprzednim kroku warto utworzyć regułę ostrzegawczą użytkowników przed otwarciem załączników z plikami Office, które zawierają makra. Oprogramowanie wymuszające okup może być ukryte w makrach, więc ostrzegaj użytkowników, aby nie otwierali tych plików przed nieumiejętną wiedzą.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWrWGt?autoplay=false]

1. W centrum administracyjnym w ujmce [https://admin.microsoft.com](https://admin.microsoft.com)wybierz pozycję **Exchange** w **obszarze Centra administracyjne**.

1. Z menu po lewej stronie wybierz pozycję **przepływ poczty e-mail**.
 
1. Na karcie Reguły wybierz strzałkę obok symbolu plus (+), a następnie wybierz pozycję **Utwórz nową regułę**.

1. Na **stronie nowa reguła** wprowadź nazwę reguły, przewiń w dół, a następnie wybierz **pozycję Więcej opcji**.

Aby utworzyć regułę transportu poczty:

1. Przejdź do centrum administracyjnego w miejscu <https://admin.microsoft.com>, a następnie wybierz pozycję **Centra administracyjne** \> **Exchange**.

2. W kategorii **przepływ poczty** e-mail wybierz **pozycję reguły**.

3. Wybierz **+** pozycję , **a następnie wybierz pozycję Utwórz nową regułę**.

4. Wybierz **pozycję Więcej** opcji u dołu okna dialogowego, aby wyświetlić pełny zestaw opcji.

5. Zastosuj do reguły ustawienia z poniższej tabeli. Użyj wartości domyślnych pozostałych ustawień, chyba że chcesz je zmienić.

6. Wybierz **Zapisz**.

|Ustawienie|Ostrzegaj użytkowników przed otwieraniem załączników Office plików|
|---|---|
|Name (Nazwa)|Reguła ochrony przed oprogramowaniem wymuszającym okup: ostrzeganie użytkowników|
|Zastosuj tę regułę, jeśli . . .|Dowolny załącznik. . . rozszerzenie pliku jest do tego dopasowania. . .|
|Określanie wyrazów lub fraz|Dodaj następujące typy plików:  <br/> dotm, docm, xlsm, sltm, xla, xlam, xll, pptm, potm, ppam, ppsm, sldm|
|Wykonaj następujące czynności. . .|Powiadamianie adresata za pomocą wiadomości|
|Podaj tekst wiadomości|Tego typu pliki nie należy otwierać u osób, których nie znasz, ponieważ mogą zawierać makra ze złośliwym kodem.|

Więcej informacji można znaleźć w następujących artykułach:

- [Oprogramowanie wymuszające okup: jak zmniejszyć ryzyko](https://www.microsoft.com/security/blog/2020/04/28/ransomware-groups-continue-to-target-healthcare-critical-services-heres-how-to-reduce-risk/)

- [Przywracanie OneDrive](https://support.microsoft.com/office/fa231298-759d-41cf-bcd0-25ac53eb8a15)

## <a name="stop-auto-forwarding-for-email"></a>Zatrzymywanie automatycznego przesyłania dalej wiadomości e-mail

Hakerzy, którzy uzyskają dostęp do skrzynki pocztowej użytkownika, mogą ukraść pocztę, ustawiając ją w celu automatycznego przesyłania dalej wiadomości e-mail. Może się to zdarzyć nawet bez wiedzy użytkownika. Aby temu zapobiec, skonfiguruj regułę przepływu poczty e-mail.

Aby utworzyć regułę transportu poczty, wykonaj następujące czynności:

1. W centrum administracyjne platformy Microsoft 365 wybierz pozycję **Centra administracyjne Exchange**\>.

2. W kategorii **przepływ poczty** e-mail wybierz **pozycję reguły**.

3. Wybierz **+** pozycję , **a następnie wybierz pozycję Utwórz nową regułę**.

4. Aby wyświetlić wszystkie opcje, wybierz pozycję **Więcej opcji** u dołu okna dialogowego.

5. Zastosuj ustawienia z poniższej tabeli. Użyj wartości domyślnych pozostałych ustawień, chyba że chcesz je zmienić.

6. Wybierz **Zapisz**.

|Ustawienie|Ostrzegaj użytkowników przed otwieraniem załączników Office plików|
|---|---|
|Name (Nazwa)|Uniemożliwianie automatycznego przesyłania poczty e-mail do domen zewnętrznych|
|Zastosuj tę regułę, jeśli...|Nadawca . . . jest zewnętrzna/wewnętrzna. . . Wewnątrz organizacji|
|Dodaj warunek|Właściwości wiadomości. . . uwzględnij typ wiadomości . . . Automatyczne przesyłanie dalej|
|Wykonaj następujące czynności...|Zablokuj wiadomość. . . odrzuć wiadomość i dołącz wyjaśnienie.|
|Podaj tekst wiadomości|Automatyczne przesyłanie dalej poczty e-mail poza tę organizację jest blokowane ze względów bezpieczeństwa.|

## <a name="protect-your-email-from-phishing-attacks"></a>Ochrona poczty e-mail przed atakami wyłudzających informacje

Jeśli skonfigurowano co najmniej jedną domenę niestandardową dla środowiska Office 365 lub Microsoft 365, możesz skonfigurować ukierunkowaną ochronę przed wyłudzaniem informacji. Ochrona przed wyłudzaniem informacji, która jest częścią usługi Microsoft Defender dla systemu Office 365, może pomóc chronić Twoją organizację przed atakami opartymi na złośliwym podszydzaniu się i innych atakach wyłudzających informacje. Jeśli nie skonfigurowano domeny niestandardowej, nie musisz tego robić.

Zalecamy wprowadzenie do tej ochrony przez utworzenie zasad chroniących najważniejszych użytkowników i domenę niestandardową.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWvt9r?autoplay=false]

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender witryny</a>.

2. Przejdź do **sekcji & e-mail i zasad** \> **& zasad** \>  \> zagrożeń zapobiegających wyłudzaniu informacji w **sekcji** Zasady.

3. Na stronie **ochrony przed wyłudzaniem** informacji wybierz pozycję **+ Utwórz**. Kreator przeprowadzi Cię przez proces definiowania zasad ochrony przed wyłudzaniem informacji.

4. Określ nazwę, opis i ustawienia zasad zgodnie z zaleceniami w poniższej tabeli. Aby uzyskać więcej szczegółowych informacji, zobacz Informacje na temat zasad ochrony przed wyłudzaniem informacji w [programie Microsoft Defender Office 365 opcje.](../../security/office-365-security/set-up-anti-phishing-policies.md)

5. Po przejrzeniu ustawień wybierz pozycję Utwórz **te zasady** lub **Zapisz** odpowiednio do potrzeb.

|Ustawienie lub opcja|Zalecane ustawienie|
|---|---|
|Name (Nazwa)|Domena i najcenniejszy personel kampanii|
|Opis|Upewnij się, że nie podszywają się najważniejsze pracownicy i nasza domena.|
|Dodawanie użytkowników w celu ochrony|Wybierz **pozycję + Dodaj warunek, adresatem jest**. Wpisz nazwy użytkowników lub wprowadź adres e-mail kandydata, menedżera kampanii i innych ważnych członków personelu. Możesz dodać maksymalnie 20 wewnętrznych i zewnętrznych adresów, które chcesz chronić przed personifikacji.|
|Dodawanie domen w celu ochrony|Wybierz **pozycję + Dodaj warunek, domena adresata to**. Wprowadź domenę niestandardową skojarzoną Microsoft 365 subskrypcji usługi, jeśli została zdefiniowana. Możesz wprowadzić więcej niż jedną domenę.|
|Wybieranie akcji|Jeśli wiadomość e-mail zostanie wysłana przez spersonifikowanego użytkownika: Wybierz pozycję Przekieruj wiadomość na inny adres e-mail **, a** następnie wpisz adres e-mail administratora zabezpieczeń. na przykład *alice<span><span>@contoso.com*. Jeśli wiadomość e-mail jest wysyłana za pomocą personifikacji domeny: Wybierz **pozycję Kwarantanna wiadomości**.|
|Inteligencja skrzynek pocztowych|Domyślnie podczas tworzenia nowych zasad ochrony przed wyłudzaniem informacji jest zaznaczona inteligencja skrzynek pocztowych. Aby uzyskać najlepsze wyniki **, pozostaw** to ustawienie wł.|
|Dodawanie zaufanych nadawców i domen|Tutaj możesz dodać własną domenę lub dowolne inne zaufane domeny.|
|Zastosowano do|Zaznacz **pozycję Domena adresata to**. W **obszarze Dowolny z nich** wybierz **pozycję Wybierz**. Wybierz **pozycję + Dodaj**. Zaznacz pole wyboru obok nazwy domeny, na przykład *contoso.<span><span> com*, na liście, a następnie wybierz pozycję **Dodaj**. Wybierz pozycję **Gotowe**.|

## <a name="watch-protect-against-malicious-attachments-and-files-with-safe-attachments"></a>Obejrzyj: Ochrona przed złośliwymi załącznikami i plikami za pomocą Sejf załączników

Osoby regularnie wysyłają, odbierają i udostępniają załączniki, takie jak dokumenty, prezentacje, arkusze kalkulacyjne i inne. Samo patrząc na wiadomość e-mail, nie zawsze łatwo jest ustalić, czy załącznik jest bezpieczny, czy złośliwy. Program Microsoft Defender for Office 365, dawniej nazywany Microsoft 365 ATP lub Zaawansowana ochrona przed zagrożeniami, zawiera ochronę załączników programu Sejf, ale ta ochrona nie jest domyślnie włączona. Zalecamy utworzenie nowej reguły w celu rozpoczęcia korzystania z tej ochrony. Ta ochrona obejmuje pliki w SharePoint, OneDrive i Microsoft Teams.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWtn3I?autoplay=false]

1. Przejdź do centrum [administracyjnego](https://admin.microsoft.com) i wybierz pozycję **Konfiguracja**.
1. Przewiń w dół **do opcji Zwiększanie ochrony przed zaawansowanymi zagrożeniami**. Wybierz **pozycję Wyświetl**, **Zarządzaj**, a następnie **bezpieczne załączniki ATP**.
1. Wybierz regułę bezpiecznych załączników, a następnie wybierz **ikonę** Edytuj.
1. Wybierz **ustawienia**, a następnie sprawdź, czy jest zaznaczona opcja Zablokuj.
1. Przewiń w dół. Wybierz **pozycję Włącz przekierowywanie** i wprowadź adres e-mail lub adres osoby, którą chcesz przejrzeć zablokowane załączniki.
1. Wybierz **pozycję dotyczy**, a następnie wybierz nazwę domeny.
1. Wybierz wszelkie dodatkowe domeny, których jesteś właścicielem (na onmicrosoft.com domenę), do których ma być stosowana reguła. Wybierz **pozycję dodaj**, a następnie **przycisk OK**.
1. Wybierz **Zapisz**.

Twoja reguła bezpiecznych załączników ATP została zaktualizowana. Teraz, gdy ochrona jest w miejscu, nie będzie można otworzyć złośliwego pliku z programów Outlook, OneDrive, SharePoint ani Teams. Pliki, których dotyczy problem, będą mieć obok nich czerwone tarcze. Jeśli ktoś spróbuje otworzyć zablokowany plik, otrzyma komunikat ostrzegawczy.

Gdy Twoje zasady będą już przez jakiś czas takie zasady, odwiedź stronę Raporty, aby sprawdzić, co zostało zeskanowane.

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalu</a> i zaloguj się przy użyciu konta administratora.

2. Przejdź do **artykułu & dotyczących** \> & dotyczących współpracy z pocztą **e-mail** **&** \> **zasady zagrożeń** \> chroniące przed złośliwym oprogramowaniem w **sekcji** Zasady.

3. Wybierz **pozycję + Utwórz** , aby utworzyć nowe zasady.

4. Zastosuj ustawienia z poniższej tabeli.

5. Po przejrzeniu ustawień wybierz pozycję **Utwórz te zasady** lub **Zapisz** odpowiednio do potrzeb.

|Ustawienie lub opcja|Zalecane ustawienie|
|---|---|
|Name (Nazwa)|Blokuj bieżące i przyszłe wiadomości e-mail za pomocą wykrytego złośliwego oprogramowania.|
|Opis|Blokuj bieżące i przyszłe wiadomości e-mail oraz załączniki za pomocą wykrytego złośliwego oprogramowania.|
|Zapisywanie załączników z nieznanym złośliwym oprogramowaniem|Wybierz **pozycję Blokuj — blokuj bieżące i przyszłe wiadomości e-mail oraz załączniki przy użyciu wykrytego złośliwego oprogramowania**.|
|Przekierowywanie załącznika przy wykrywaniu|Włącz przekierowywanie (zaznacz to pole) Wprowadź konto administratora lub konfigurację skrzynki pocztowej do kwarantanny.          Zastosowanie powyższej opcji w przypadku przecowania czasu lub błędu podczas skanowania w poszukiwaniu załączników (zaznacz to pole).|
|Zastosowano do|Domeną adresata jest . . . wybierz domenę.|

Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w programie Microsoft Defender dla Office 365](../../security/office-365-security/set-up-anti-phishing-policies.md).

## <a name="protect-against-phishing-attacks-with-safe-links"></a>Ochrona przed atakami wyłudzających informacje za pomocą Sejf informacji

Hakerzy czasami ukrywają złośliwe witryny internetowe w linkach w wiadomościach e-mail lub innych plikach. Sejf Links, część usługi Microsoft Defender dla Office 365, może pomóc chronić Twoją organizację, udostępniając weryfikację adresów internetowych (adresów URL) za pomocą kliknięcia w wiadomościach e-mail i Office dokumentach. Ochrona jest definiowana za pomocą Sejf linków sieciowych.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWvdwy?autoplay=false]

Program Microsoft Defender Office 365, dawniej nazywany Microsoft 365 ATP lub Zaawansowana ochrona przed zagrożeniami, pomaga chronić firmę przed złośliwymi witrynami, gdy użytkownik klika linki w Office aplikacjach.

1. Przejdź do centrum [administracyjnego](https://admin.microsoft.com) i wybierz pozycję **Konfiguracja**.

1. Przewiń w dół **do opcji Zwiększanie ochrony przed zaawansowanymi zagrożeniami**. Wybierz **pozycję Zarządzaj**, a następnie **Sejf linki**.

1. Wybierz **pozycję Ustawienia** globalne i **w polu Blokuj następujące adresy URL** wprowadź adres URL, który chcesz zablokować.

Zalecamy:

- Zmodyfikuj zasady domyślne, aby zwiększyć ochronę.

- Dodaj nowe zasady kierowane do wszystkich adresatów w domenie.

Aby skonfigurować linki Sejf, wykonaj następujące czynności:

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalu</a> i zaloguj się przy użyciu konta administratora.

2. o na **wiadomości e-& zasad współpracy &** \> **zasad** \> **zagrożeń** \> chroniących **przed** złośliwym oprogramowaniem w **sekcji** Zasady.

3. Wybierz **pozycję + Utwórz** , aby utworzyć nowe zasady, lub zmodyfikuj zasady domyślne.

Aby zmodyfikować zasady domyślne:

1. Kliknij dwukrotnie zasady **Domyślne** . Zostanie wyświetlone wysuw. 

2. Wybierz **pozycję Edytuj ustawienia ochrony** u dołu wysuwu.

3. Po zmodyfikowaniu zasad domyślnych wybierz pozycję **Zapisz**.

|Ustawienie lub opcja|Zalecane ustawienie|
|---|---|
|Name (Nazwa)|Sejf linków dla wszystkich adresatów w domenie|
|Wybierz akcję dla nieznanych, potencjalnie złośliwych adresów URL w wiadomościach|Wybierz **pozycję W — po kliknięciu linku** adresy URL będą ponownie pisane i sprawdzane pod kątem listy znanych złośliwych linków.|
|Używanie załączników Sejf do skanowania zawartości do pobrania|Zaznacz to pole.|
|Zastosowano do|Domeną adresata jest . . . wybierz domenę.|

Aby uzyskać więcej informacji, zobacz [Sejf linków](../../security/office-365-security/safe-links.md).

## <a name="go-to-intune-admin-center"></a>Przejdź do centrum administracyjnego usługi Intune

1. Zaloguj się do [portalu Azure Portal](https://portal.azure.com/).

2. Wybierz **pozycję Wszystkie usługi** i wpisz *intune* w **polu wyszukiwania**.

3. Po wyświetlonej liście wyników wybierz początek obok **Microsoft Intune, aby** dodać go do ulubionych i ułatwić jego późniejsze znalezienie.

Oprócz centrum administracyjnego do rejestrowania urządzeń organizacji i zarządzania nimi możesz użyć usługi Intune. Aby uzyskać więcej informacji, zobacz Funkcje według [metody rejestracji Windows urządzeń](/intune/enrollment/enrollment-method-capab) i Opcje rejestracji dla urządzeń [zarządzanych przez usługę Intune](/intune/enrollment-options).
