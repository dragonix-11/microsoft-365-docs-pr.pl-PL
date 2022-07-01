---
title: Najlepsze rozwiązania dotyczące zabezpieczania platformy Microsoft 365 dla firm
f1.keywords:
- CSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
- admindeeplinkDEFENDER
- adminvideo
- admindeeplinkEXCHANGE
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: de2da300-dbb6-4725-bb12-b85a9d296e75
description: Ochrona firmowych wiadomości e-mail i danych przed zagrożeniami cybernetycznymi, w tym oprogramowaniem wymuszającym okup, wyłudzaniem informacji i złośliwymi załącznikami.
ms.openlocfilehash: 347d88a95d8ed55116655980560eb3d9cf925213
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2022
ms.locfileid: "66602939"
---
# <a name="best-practices-for-securing-microsoft-365-for-business"></a>Najlepsze rozwiązania dotyczące zabezpieczania platformy Microsoft 365 dla firm

Zapoznaj się z [pomocą dla małych firm platformy Microsoft 365](https://go.microsoft.com/fwlink/?linkid=2197659) w serwisie YouTube.

Jeśli jesteś małą lub średnią organizacją korzystającą z jednego z planów biznesowych firmy Microsoft, wskazówki zawarte w tym artykule ułatwiają zaostrzenie zabezpieczeń organizacji. Wśród twoich wyborów Microsoft 365 Business Premium jest liderem, ponieważ obecnie obejmuje Microsoft Defender dla Firm i inne [zabezpieczenia](../../business-premium/get-microsoft-365-business-premium.md). Zalecane działania zawarte w tym miejscu pomogą Ci osiągnąć cele opisane w [podręczniku Kampanii Cyberbezpieczeństwa](https://go.microsoft.com/fwlink/p/?linkid=2015598) Harvard Kennedy School.

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczącej kroków opisanych w tym artykule, rozważ [współpracę ze specjalistą ds. małych firm firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej uzyskasz wraz ze swoimi pracownikami całodobowy dostęp do wsparcia ze strony specjalistów ds. małych firm potrzebnego w miarę rozwoju Twojej firmy — od dołączania po codzienne użytkowanie.

## <a name="watch-a-quick-overview-of-security"></a>Obejrzyj: Krótkie omówienie zabezpieczeń

Zapoznaj się z tym filmem i innymi osobami na naszym [kanale YouTube](https://go.microsoft.com/fwlink/?linkid=2198012).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4mzxI?autoplay=false]

Wszystkie plany platformy Microsoft 365 oferują podstawową ochronę i zabezpieczenia za pomocą programu antywirusowego Defender, ale dzięki Microsoft 365 Business Premium masz również funkcje ochrony przed zagrożeniami, ochrony danych i zarządzania urządzeniami ze względu na włączenie Microsoft Defender dla Firm.  Te dodatkowe funkcje chronią organizację przed zagrożeniami online i nieautoryzowanym dostępem, a także umożliwiają zarządzanie danymi firmowymi na telefonach, tabletach i komputerach.

## <a name="security-features-comparison"></a>Porównanie funkcji zabezpieczeń

Aby dowiedzieć się więcej o jednej z funkcji planu usługi, kliknij nagłówek w poniższej tabeli. 

|Zadanie|Microsoft 365 Business Standard|Microsoft 365 Business Premium|
|---|---|---|
[Ochrona przed utratą lub kradzieżą haseł](#set-up-multi-factor-authentication) | ![Zawarte.](../../media/d238e041-6854-4a78-9141-049224df0795.png) | ![Zawarte.](../../media/d238e041-6854-4a78-9141-049224df0795.png) |
[Szkolenie użytkowników](#train-your-users) | ![Zawarte.](../../media/d238e041-6854-4a78-9141-049224df0795.png) | ![Zawarte.](../../media/d238e041-6854-4a78-9141-049224df0795.png) |
[Korzystanie z dedykowanych kont administratorów](#use-dedicated-admin-accounts)|![Zawarte.](../../media/d238e041-6854-4a78-9141-049224df0795.png) | ![Zawarte.](../../media/d238e041-6854-4a78-9141-049224df0795.png) | 
[Ochrona przed złośliwym oprogramowaniem](#protect-against-malware) | ![Zawarte.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(ochrona poczty e-mail) | ![Zawarte.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(zwiększona ochrona poczty e-mail i urządzeń) |
[Ochrona przed oprogramowaniem wymuszającym okup](#protect-against-ransomware) | ![Zawarte.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(ochrona poczty e-mail i magazynu w chmurze) | ![Zawarte.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(zwiększona ochrona urządzeń, poczty e-mail i magazynu w chmurze) |
[Szyfrowanie poufnych wiadomości e-mail](#send-encrypted-email) | ![Zawarte.](../../media/d238e041-6854-4a78-9141-049224df0795.png) | ![Zawarte.](../../media/d238e041-6854-4a78-9141-049224df0795.png) |
[Ochrona poczty e-mail przed atakami wyłudzania informacji](#protect-sensitive-emails) | ![Zawarte.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(ochrona przed wyłudzaniem informacji) | ![Zawarte.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(zaawansowana ochrona przed wyłudzaniem informacji) |
[Ochrona przed złośliwymi załącznikami, plikami i adresami URL w wiadomościach e-mail i plikach pakietu Office](#protect-against-malicious-attachments-files-and-urls) | | ![Zawarte.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(Bezpieczne linki i bezpieczne załączniki) |
[Zwiększanie ochrony urządzeń organizacji](#increase-protection-for-your-organizations-devices) | | ![Zawarte.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(ochrona urządzeń klasy korporacyjnej) |

Możesz szybko skonfigurować zabezpieczenia i rozpocząć bezpieczną współpracę, korzystając ze wskazówek podanych w bibliotece [Microsoft 365 Business Premium](../../business-premium/index.md). Informacje business premium zostały opracowane we współpracy z zespołem Microsoft Defending Democracy, aby chronić wszystkich małych klientów biznesowych przed zagrożeniami cybernetycznymi, które są uruchamiane przez zaawansowane cyberataki i hakerów.

### <a name="about-the-microsoft-365-secure-score"></a>Informacje o wskaźniku bezpieczeństwa platformy Microsoft 365

Ważne jest, aby przed rozpoczęciem sprawdzić wskaźnik bezpieczeństwa platformy [Microsoft 365](../../security/defender/microsoft-secure-score.md) w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a>. Ze scentralizowanego pulpitu nawigacyjnego można monitorować i ulepszać zabezpieczenia tożsamości, danych, aplikacji, urządzeń i infrastruktury platformy Microsoft 365. Otrzymujesz punkty dotyczące konfigurowania zalecanych funkcji zabezpieczeń, wykonywania zadań związanych z zabezpieczeniami (takich jak wyświetlanie raportów) lub rozwiązywania problemów z zaleceniami za pomocą aplikacji lub oprogramowania innej firmy. Dzięki dodatkowym szczegółowym informacjom i większej widoczności szerszego zestawu produktów i usług firmy Microsoft możesz mieć pewność raportowania kondycji zabezpieczeń organizacji.

![Zrzut ekranu przedstawiający wskaźnik bezpieczeństwa firmy Microsoft.](../../media/secure-score.png)

## <a name="set-up-multi-factor-authentication"></a>Konfigurowanie uwierzytelniania wieloskładnikowego

Ochrona przed utratą lub kradzieżą haseł przy użyciu uwierzytelniania wieloskładnikowego (MFA). Skonfigurowanie uwierzytelniania wieloskładnikowego wymaga od użytkowników użycia kodu na telefonie w celu zalogowania się do platformy Microsoft 365. Ten dodatkowy krok może uniemożliwić hakerom przejęcie kontroli, jeśli znają Twoje hasło. 

Uwierzytelnianie wieloskładnikowe jest również nazywane weryfikacją dwuetapową. Osoby fizyczne mogą łatwo dodać weryfikację dwuetapową do większości kont, na przykład do kont Google lub Microsoft. Poniżej przedstawiono sposób [dodawania weryfikacji dwuetapowej do osobistego konta Microsoft](https://go.microsoft.com/fwlink/p/?linkid=2016403).

W przypadku firm korzystających z platformy Microsoft 365 dodaj ustawienie, które wymaga od użytkowników zalogowania się przy użyciu uwierzytelniania wieloskładnikowego. Po wprowadzeniu tej zmiany użytkownicy będą monitować o skonfigurowanie telefonu do uwierzytelniania dwuskładnikowego przy następnym logowaniu.
Aby wyświetlić wideo szkoleniowe dotyczące sposobu konfigurowania uwierzytelniania wieloskładnikowego i sposobu ukończenia konfiguracji przez użytkowników, zobacz [Konfigurowanie uwierzytelniania wieloskładnikowego](set-up-multi-factor-authentication.md) i [konfigurowania użytkowników](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14).

### <a name="turn-on-security-defaults"></a>Włączanie ustawień domyślnych zabezpieczeń

W przypadku większości organizacji wartości domyślne zabezpieczeń oferują dobry poziom dodatkowych zabezpieczeń logowania. Aby uzyskać więcej informacji, zobacz [Co to są ustawienia domyślne zabezpieczeń?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults). Jeśli subskrypcja jest nowa, ustawienia domyślne zabezpieczeń mogą być już włączone automatycznie.

Włącz lub wyłącz wartości domyślne zabezpieczeń w okienku **Właściwości** usługi Azure Active Directory (Azure AD) w Azure Portal.

1. Zaloguj się do [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) przy użyciu poświadczeń administratora globalnego.

2. W lewym okienku nawigacji wybierz pozycję **Pokaż wszystko** i w obszarze **Administracja center** wybierz pozycję **Azure Active Directory**.

3. W **centrum administracyjnym usługi Azure Active Directory** wybierz pozycję **Właściwości** **usługi Azure Active Directory** > .

4. W dolnej części strony wybierz pozycję **Zarządzanie wartościami domyślnymi zabezpieczeń**.

5. Wybierz pozycję **Tak** , aby włączyć ustawienia domyślne zabezpieczeń lub **Nie** , aby wyłączyć wartości domyślne zabezpieczeń, a następnie wybierz pozycję **Zapisz**.

Po skonfigurowaniu uwierzytelniania wieloskładnikowego w organizacji użytkownicy będą musieli skonfigurować weryfikację dwuetapową na swoich urządzeniach. Aby uzyskać więcej informacji, zobacz [Konfigurowanie weryfikacji dwuetapowej dla platformy Microsoft 365](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14).

> [!Tip]
> Jeśli potrzebujesz bardziej szczegółowej kontroli nad uwierzytelnianiem wieloskładnikowym, możesz włączyć dostęp warunkowy przy użyciu Microsoft 365 Business Premium. W takim przypadku zalecamy zaimplementowanie równoważnych zasad z wartościami domyślnymi zabezpieczeń. Przejdź tutaj, aby uzyskać więcej informacji na temat [ustawień domyślnych zabezpieczeń](/microsoft-365/business-premium/m365bp-conditional-access).

Aby uzyskać więcej szczegółów i zaleceń, zobacz [Konfigurowanie uwierzytelniania wieloskładnikowego dla użytkowników](set-up-multi-factor-authentication.md).

## <a name="train-your-users"></a>Szkolenie użytkowników

[Podręcznik kampanii cyberbezpieczeństwa](https://go.microsoft.com/fwlink/p/?linkid=2015598) Harvard Kennedy School zawiera doskonałe wskazówki dotyczące ustanawiania silnej kultury świadomości bezpieczeństwa w organizacji, w tym szkolenia użytkowników w celu identyfikowania ataków wyłudzających informacje.

Ponadto firma Microsoft zaleca użytkownikom podjęcie działań opisanych w tym artykule: [Ochrona konta i urządzeń przed hakerami i złośliwym oprogramowaniem](https://support.microsoft.com/office/066d6216-a56b-4f90-9af3-b3a1e9a327d6). Te akcje obejmują:

- Używanie silnych haseł
- Ochrona urządzeń
- Włączanie funkcji zabezpieczeń na komputerach Windows 10 i Mac

Firma Microsoft zaleca również, aby użytkownicy chronili swoje osobiste konta e-mail, wykonując akcje zalecane w następujących artykułach:

- [Ochrona konta e-mail Outlook.com](https://support.microsoft.com/office/a4f20fc5-4307-4ece-8231-6d4d4bd8a9ba)

- [Ochrona konta Gmail za pomocą weryfikacji dwuetapowej](https://go.microsoft.com/fwlink/p/?linkid=2015688&)

## <a name="use-dedicated-admin-accounts"></a>Korzystanie z dedykowanych kont administratorów

Konta administracyjne używane do administrowania środowiskiem platformy Microsoft 365 obejmują podwyższone uprawnienia. Są to cenne cele dla hakerów i cyberataków. Używaj kont administratora tylko do administrowania. Administratorzy powinni mieć oddzielne konto użytkownika do regularnego, nieadministracyjnyego użytku i używać konta administracyjnego tylko wtedy, gdy jest to konieczne do wykonania zadania skojarzonego z funkcją zadania. Dodatkowe zalecenia:

- Upewnij się, że konta zostały dodane do [usługi Azure Active Directory](../../admin/add-users/add-users.md).
- Upewnij się, że konta administratorów są również skonfigurowane do uwierzytelniania wieloskładnikowego.
- Przed użyciem kont administratorów zamknij wszystkie niepowiązane sesje przeglądarki i aplikacje, w tym osobiste konta e-mail.
- Po wykonaniu zadań administratora wyloguj się z sesji przeglądarki.

## <a name="protect-against-malware"></a>Ochrona przed złośliwym oprogramowaniem

Środowisko platformy Microsoft 365 obejmuje ochronę przed złośliwym oprogramowaniem. Ochronę przed złośliwym oprogramowaniem można zwiększyć, wykonując następujące czynności:

- Używanie [wstępnie ustawionych zasad dla Microsoft Office 365](../../../microsoft-365/security/office-365-security/preset-security-policies.md).
- Blokowanie załączników z określonymi typami plików.
- Korzystanie z ochrony antywirusowej/ochrony przed złośliwym oprogramowaniem na urządzeniach, zwłaszcza Microsoft Defender dla Firm. Zawiera funkcje, takie jak [automatyczne raportowanie śledcze](../../security/office-365-security/air-view-investigation-results.md) (AIR) i pulpit nawigacyjny zarządzania zagrożeniami i lukami w zabezpieczeniach (TVM). Gdy Microsoft Defender dla Firm nie jest podstawowym oprogramowaniem antywirusowym, nadal można go uruchomić w trybie pasywnym i używać [ochrony punktów końcowych i odpowiedzi (EDR),](../../security/defender-endpoint/overview-endpoint-detection-response.md) zwłaszcza w [trybie bloku](../../security/defender-endpoint/edr-in-block-mode.md), w którym działa w tle w celu skorygowania złośliwych artefaktów, które zostały wykryte przez możliwości EDR i pominięte przez podstawowe oprogramowanie do wykrywania wirusów.

### <a name="block-attachments-with-certain-file-types"></a>Blokuj załączniki z określonymi typami plików

Ochronę przed złośliwym oprogramowaniem można zwiększyć, blokując załączniki z typami plików, które są często używane w przypadku złośliwego oprogramowania. Aby zwiększyć ochronę przed złośliwym oprogramowaniem w wiadomości e-mail, zobacz [Obejrzyj: Podnieś poziom ochrony przed złośliwym oprogramowaniem w wiadomości e-mail](increase-threat-protection.md#watch-raise-the-level-of-protection-against-malware-in-mail) lub wykonaj następujące kroki:

1. W <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender przejdź do obszaru</a> Zasady **współpracy** \> & poczty e-mail **& reguły** \> **Zasady** \> zagrożeń **Chroniące przed złośliwym oprogramowaniem** w sekcji **Zasady**.
2. Na stronie **Ochrona przed złośliwym oprogramowaniem** kliknij dwukrotnie pozycję **Domyślne**. Zostanie wyświetlone okno wysuwane.
3. Wybierz pozycję **Edytuj ustawienia ochrony** w dolnej części okna wysuwanego.
4. Na następnej stronie w obszarze **Ustawienia ochrony** zaznacz pole wyboru obok pozycji **Włącz filtr wspólnych załączników**. Zablokowane typy plików są wyświetlane bezpośrednio poniżej tej opcji. Aby dodać lub usunąć typy plików, wybierz pozycję **Dostosuj typy plików** na końcu listy.
5. Wybierz **Zapisz**.

Aby uzyskać więcej informacji, zobacz [Ochrona przed złośliwym kodem w usłudze EOP](../../security/office-365-security/anti-malware-protection.md).

### <a name="use-antivirus-and-anti-malware-protection"></a>Korzystanie z ochrony antywirusowej i ochrony przed złośliwym oprogramowaniem

Program antywirusowy Microsoft Defender zapewnia silne oprogramowanie antywirusowe i ochronę przed złośliwym kodem oraz jest wbudowany w system operacyjny Windows.

Jeśli Twoja organizacja korzysta z Microsoft 365 Business Premium, uzyskasz dodatkową ochronę urządzenia, która obejmuje:

- Ochrona nowej generacji
- Ochrona zapory
- Filtrowanie zawartości sieci Web

Te możliwości są dostępne w Microsoft Defender dla Firm— ofercie, która rozpocznie się dla Microsoft 365 Business Premium klientów, począwszy od 1 marca 2022 r.

[Dowiedz się więcej o Microsoft Defender dla Firm](../../security/defender-business/mdb-overview.md).

## <a name="protect-against-ransomware"></a>Ochrona przed oprogramowaniem wymuszającym okup

Oprogramowanie wymuszające okup ogranicza dostęp do danych przez szyfrowanie plików lub blokowanie ekranów komputerów. Następnie próbuje wyłudzać pieniądze od ofiar, prosząc o "okup", zwykle w formie kryptowalut, takich jak Bitcoin, w zamian za dostęp do danych.

Ochrona przed oprogramowaniem wymuszającym okup dla poczty e-mail hostowanej na platformie Microsoft 365 i plików przechowywanych w usłudze OneDrive. Jeśli masz Microsoft 365 Business Premium, uzyskasz dodatkową ochronę przed oprogramowaniem wymuszającym okup dla urządzeń organizacji.

Możesz chronić się przed oprogramowaniem wymuszającym okup, tworząc co najmniej jedną regułę przepływu poczty, aby zablokować rozszerzenia plików, które są często używane do wymuszania okupu, lub ostrzegać użytkowników, którzy otrzymują te załączniki w wiadomości e-mail. Dobrym punktem wyjścia jest utworzenie dwóch reguł:

- Używaj usługi OneDrive do przenoszenia plików, aby zawsze były kontrolowane i chronione.

- Ostrzegaj użytkowników przed otwarciem załączników plików pakietu Office zawierających makra. Oprogramowanie wymuszające okup może być ukryte wewnątrz makr, więc ostrzegamy użytkowników, aby nie otwierali tych plików od osób, których nie znają.

- Blokuj typy plików, które mogą zawierać oprogramowanie wymuszające okup lub inny złośliwy kod. Zaczniemy od wspólnej listy plików wykonywalnych (wymienionych w poniższej tabeli). Jeśli organizacja używa dowolnego z tych typów plików wykonywalnych i oczekujesz, że zostaną one wysłane w wiadomości e-mail, dodaj je do poprzedniej reguły (ostrzegaj użytkowników).

Aby utworzyć regułę transportu poczty, wyświetl widok [Obejrzyj: Ochrona przed oprogramowaniem wymuszającym okup](increase-threat-protection.md#watch-protect-against-ransomware) lub wykonaj następujące kroki:

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centrum administracyjnego programu Exchange</a>.

2. W kategorii **przepływ poczty** wybierz **reguły**.

3. Wybierz pozycję **+**, a następnie **pozycję Utwórz nową regułę**.

4. Wybierz pozycję **** w dolnej części okna dialogowego, aby wyświetlić pełny zestaw opcji.

5. Zastosuj ustawienia w poniższej tabeli dla każdej reguły. Pozostaw pozostałe ustawienia jako domyślne, chyba że chcesz je zmienić.

6. Wybierz **Zapisz**.

| Ustawienie | Ostrzegaj użytkowników przed otwarciem załączników plików pakietu Office | Blokuj typy plików, które mogą zawierać oprogramowanie wymuszające okup lub inny złośliwy kod |
|:-----|:-----|:-----|
|Name (Nazwa)  <br/> |Reguła ochrony przed oprogramowaniem wymuszającym okup: ostrzegaj użytkowników  <br/> |Reguła ochrony przed oprogramowaniem wymuszającym okup: typy plików blokowych  <br/> |
|Zastosuj tę regułę, jeśli . . .  <br/> |Dowolny załącznik . . . rozszerzenie pliku jest zgodne z . . .  <br/> |Dowolny załącznik . . . rozszerzenie pliku jest zgodne z . . .  <br/> |
|Określanie wyrazów lub fraz  <br/> |Dodaj następujące typy plików:  <br/> dotm, docm, xlsm, sltm, xla, xlam, xll, pptm, potm, ppam, ppsm, sldm  <br/> |Dodaj następujące typy plików:  <br/> ade, adp, ani, bas, bat, chm, cmd, com, cpl, crt, hlp, ht, hta, inf, ins, isp, job, jse, jse, lnk, mda, mdb, mde, mdz, msc, msi, msp, mst, pcd, reg, scr, sct, shs, url, vb, vbe, vbs, wsc, wsf, wsh, exe, pif  <br/> |
|Wykonaj następujące czynności. . .  <br/> |Przedsąd zastrzeżenia  <br/> |Zablokuj komunikat . . . odrzuć komunikat i dołącz wyjaśnienie  <br/> |
|Podaj tekst wiadomości  <br/> |Nie otwieraj tych typów plików — chyba że ich oczekiwano — ponieważ pliki mogą zawierać złośliwy kod, a wiedza o nadawcy nie jest gwarancją bezpieczeństwa.  <br/> ||

> [!TIP]
> Możesz również dodać pliki, które chcesz zablokować, do listy ochrony przed złośliwym [oprogramowaniem w sekcji Ochrona przed złośliwym oprogramowaniem](#protect-against-malware).

Więcej informacji można znaleźć w następujących artykułach:

- [Oprogramowanie wymuszające okup: jak zmniejszyć ryzyko](https://www.microsoft.com/security/blog/2020/04/28/ransomware-groups-continue-to-target-healthcare-critical-services-heres-how-to-reduce-risk/)

- [Lepiej razem: program antywirusowy Microsoft Defender i usługa Office 365](../../security/defender-endpoint/office-365-microsoft-defender-antivirus.md)

- [Przywracanie usługi OneDrive](https://support.microsoft.com/office/fa231298-759d-41cf-bcd0-25ac53eb8a15)


## <a name="protect-sensitive-emails"></a>Ochrona poufnych wiadomości e-mail

Platforma Microsoft 365 obejmuje szyfrowanie komunikatów pakietu Office, które umożliwia wysyłanie i odbieranie zaszyfrowanych wiadomości e-mail między osobami w organizacji i poza nią, a tylko zamierzoni adresaci mogą je wyświetlać. Szyfrowanie działa z usługami Outlook.com, Yahoo!, Gmail i innymi usługami poczty e-mail.

> [!Tip]
> Jeśli wymagany jest bardziej rygorystyczny poziom zabezpieczeń, organizacja powinna również skonfigurować i używać etykietowania poufności dla wiadomości e-mail lub plików. [Etykiety poufności](../../compliance/sensitivity-labels.md) umożliwiają kontrolę nad zawartością, bez względu na to, dokąd zmierza.

### <a name="send-encrypted-email"></a>Wysyłanie zaszyfrowanej wiadomości e-mail

Aby zaszyfrować wiadomość e-mail:

1. Po otwarciu nowej wiadomości e-mail wybierz menu **Opcje** .
1. Z listy rozwijanej **Szyfruj** wybierz odpowiedni poziom uprawnień.

:::image type="content" source="../../media/08e90a7e-a2d2-41a4-bae9-0a46b4ce639b.png" alt-text="Szyfrowanie wiadomości e-mail w programie Outlook":::

### <a name="receive-encrypted-email"></a>Odbieranie zaszyfrowanej wiadomości e-mail

Jeśli adresat ma program Outlook 2013 lub Outlook 2016 i konto e-mail firmy Microsoft, zobaczy alert dotyczący ograniczonych uprawnień elementu w okienku Odczyt. Po otwarciu wiadomości adresat może wyświetlić komunikat tak samo jak każdy inny.

Jeśli adresat korzysta z innego klienta poczty e-mail lub konta e-mail, takiego jak Gmail lub Yahoo, zobaczy link umożliwiający zalogowanie się w celu odczytania wiadomości e-mail lub zażądanie jednorazowego kodu dostępu w celu wyświetlenia wiadomości w przeglądarce internetowej. Jeśli użytkownicy nie otrzymują wiadomości e-mail, powinni sprawdzić folder Spam lub Wiadomości-śmieci.

> [!TIP]
> Aby uzyskać więcej informacji, zobacz [Wysyłanie, wyświetlanie i odpowiadanie na zaszyfrowane wiadomości w programie Outlook dla komputerów PC](https://support.microsoft.com/office/eaa43495-9bbb-4fca-922a-df90dee51980).

## <a name="protect-the-organization"></a>Ochrona organizacji

Jeśli skonfigurowano co najmniej jedną domenę niestandardową dla środowiska platformy Microsoft 365, możesz skonfigurować ukierunkowaną ochronę przed wyłudzaniem informacji. Ochrona przed wyłudzaniem informacji jest uwzględniona w Ochrona usługi Office 365 w usłudze Microsoft Defender i może pomóc chronić organizację przed złośliwym wyłudzaniem informacji opartym na personifikacji i innymi atakami.

> [!Note]
> Jeśli domena niestandardowa nie została skonfigurowana, nie musisz tego robić.

Zalecamy rozpoczęcie pracy z tą ochroną przez utworzenie zasad dla najważniejszych użytkowników i domeny niestandardowej. Dobrym miejscem do tego jest Microsoft 365 Defender, dołączone do usługi Microsoft Business Premium. Aby utworzyć zasady ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender, wykonaj następujące kroki:

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a>.

2. Przejdź do **obszaru Zasady współpracy** \> & poczty e-mail **, & reguły** \> **zasady** \> zagrożeń **— ochrona przed wyłudzaniem informacji** w sekcji **Zasady** .

3. Na stronie Ochrona przed wyłudzaniem informacji wybierz pozycję **+ Utwórz**. Zostanie uruchomiony kreator, który przeprowadzi Cię przez zdefiniowanie zasad ochrony przed wyłudzaniem informacji.

4. Określ nazwę, opis i ustawienia zasad zgodnie z zaleceniami na poniższym wykresie. Aby uzyskać więcej informacji, zobacz [Informacje o zasadach ochrony przed wyłudzaniem informacji w opcjach Ochrona usługi Office 365 w usłudze Microsoft Defender](../../security/office-365-security/set-up-anti-phishing-policies.md).

5. Po przejrzeniu ustawień wybierz odpowiednio pozycję **Utwórz te zasady** lub **Zapisz**.

|Ustawienie lub opcja|Zalecane ustawienie|
|---|---|
|Name (Nazwa)|Domena i najcenniejszy personel kampanii|
|Opis|Upewnij się, że najważniejszy personel i nasza domena nie są personifikowane.|
|Dodawanie użytkowników w celu ochrony|Wybierz **pozycję + Dodaj warunek. Adresat to**. Wpisz nazwy użytkowników lub wprowadź adres e-mail kandydata, kierownika kampanii i innych ważnych pracowników. Możesz dodać maksymalnie 20 adresów wewnętrznych i zewnętrznych, które chcesz chronić przed personifikacją.|
|Dodawanie domen w celu ochrony|Wybierz **pozycję + Dodaj warunek. Domena adresata to**. Wprowadź domenę niestandardową skojarzoną z subskrypcją platformy Microsoft 365, jeśli została zdefiniowana. Możesz wprowadzić więcej niż jedną domenę.|
|Wybieranie akcji|Jeśli wiadomość e-mail jest wysyłana przez personifikowanego użytkownika: wybierz pozycję **Przekieruj wiadomość na inny adres e-mail**, a następnie wpisz adres e-mail administratora zabezpieczeń; na przykład securityadmin@contoso.com. <br/> Jeśli wiadomość e-mail jest wysyłana przez domenę personifikaną: wybierz pozycję **Wiadomość kwarantanny**.|
|Analiza skrzynki pocztowej|Domyślnie funkcja analizy skrzynek pocztowych jest wybierana podczas tworzenia nowych zasad ochrony przed wyłudzaniem informacji. Pozostaw to ustawienie **Włączone** , aby uzyskać najlepsze wyniki.|
|Dodawanie zaufanych nadawców i domen|W tym przykładzie nie należy definiować żadnych przesłoń.|
|Zastosowane do|Wybierz **pozycję Domena adresata.** W obszarze **Dowolne z nich** wybierz pozycję **Wybierz**. Wybierz pozycję **+ Dodaj**. Zaznacz pole wyboru obok nazwy domeny, na przykład contoso.com, na liście, a następnie wybierz pozycję **Dodaj**. Wybierz pozycję **Gotowe**.|

> [!TIP]
> Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender](../../security/office-365-security/configure-atp-anti-phishing-policies.md).

## <a name="protect-against-malicious-attachments-files-and-urls"></a>Ochrona przed złośliwymi załącznikami, plikami i adresami URL

Osoby regularnie wysyłają, odbierają i udostępniają załączniki, takie jak dokumenty, prezentacje, arkusze kalkulacyjne i inne. Nie zawsze łatwo jest stwierdzić, czy załącznik jest bezpieczny, czy złośliwy, patrząc na wiadomość e-mail. Ochrona usługi Office 365 w usłudze Microsoft Defender obejmuje ochronę bezpiecznych załączników, ale ta ochrona nie jest domyślnie włączona. Zalecamy utworzenie nowej reguły, aby rozpocząć korzystanie z tej ochrony. Ta ochrona obejmuje pliki w programach SharePoint, OneDrive i Microsoft Teams.

### <a name="set-up-safe-attachments"></a>Konfigurowanie bezpiecznych załączników

Możesz użyć wstępnie ustawionych zasad bezpiecznych załączników lub utworzyć własne. Aby utworzyć zasady bezpiecznych załączników, wyświetl [krótki film szkoleniowy](increase-threat-protection.md) lub wykonaj następujące kroki:

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a> i zaloguj się przy użyciu konta administratora.

2. Przejdź do **obszaru Zasady współpracy** \> & poczty e-mail **& reguły** \> Zasady \> **zagrożeń** **Chroniące przed złośliwym oprogramowaniem** w sekcji **Zasady**.

3. Wybierz pozycję **+ Utwórz** , aby utworzyć nowe zasady.

4. Zastosuj ustawienia w poniższej tabeli.

5. Po przejrzeniu ustawień wybierz odpowiednio pozycję **Utwórz te zasady** lub **Zapisz**.

|Ustawienie lub opcja|Zalecane ustawienie|
|---|---|
|Name (Nazwa)|Blokuj bieżące i przyszłe wiadomości e-mail z wykrytym złośliwym oprogramowaniem.|
|Opis|Blokuj bieżące i przyszłe wiadomości e-mail i załączniki przy użyciu wykrytego złośliwego oprogramowania.|
|Zapisywanie załączników — nieznana odpowiedź na złośliwe oprogramowanie|Wybierz pozycję **Blokuj — blokuj bieżące i przyszłe wiadomości e-mail i załączniki przy użyciu wykrytego złośliwego oprogramowania**.|
|Przekierowywanie załącznika po wykryciu|Włącz przekierowanie (zaznacz to pole) <br/> Wprowadź konto administratora lub konfigurację skrzynki pocztowej na potrzeby kwarantanny. <br/> Zastosuj powyższe zaznaczenie, jeśli skanowanie pod kątem złośliwego oprogramowania w poszukiwaniu załączników przekroczy limit czasu lub wystąpi błąd (zaznacz to pole).|
|Zastosowane do|Domena adresata to . . . wybierz domenę.|

> [!TIP]
> Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender](../../security/office-365-security/configure-atp-anti-phishing-policies.md).

### <a name="set-up-safe-links"></a>Konfigurowanie bezpiecznych linków

Hakerzy czasami ukrywają złośliwe witryny internetowe w linkach w wiadomościach e-mail lub innych plikach. Bezpieczne linki, część Ochrona usługi Office 365 w usłudze Microsoft Defender, mogą pomóc w ochronie organizacji, zapewniając weryfikację adresów internetowych (adresów URL) w wiadomościach e-mail i dokumentach pakietu Office. Ochrona jest definiowana za pomocą zasad bezpiecznych linków.

Wykonaj następujące czynności, aby chronić przed atakami:

- Zmodyfikuj zasady domyślne, aby zwiększyć ochronę.

- Dodaj nowe zasady przeznaczone dla wszystkich adresatów w domenie.

Aby uzyskać dostęp do bezpiecznych linków, zobacz [Obejrzyj: Ochrona poczty e-mail przed atakami wyłudzania informacji](increase-threat-protection.md#watch-protect-your-email-from-phishing-attacks) lub wykonaj następujące kroki:

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a> i zaloguj się przy użyciu konta administratora.

2. Przejdź do **obszaru Zasady współpracy** \> & poczty e-mail **& reguły** \> Zasady \> **zagrożeń** **Chroniące przed złośliwym oprogramowaniem** w sekcji **Zasady**.

3. Wybierz pozycję **+ Utwórz** , aby utworzyć nowe zasady, lub zmodyfikuj zasady domyślne.

Aby zmodyfikować zasady domyślne:

1. Kliknij dwukrotnie zasady **domyślne** . Zostanie wyświetlone okno wysuwane. 

2. Wybierz pozycję **Edytuj ustawienia ochrony** w dolnej części okna wysuwanego.

3. Po zmodyfikowaniu zasad domyślnych wybierz pozycję **Zapisz**.

|Ustawienie lub opcja|Zalecane ustawienie|
|---|---|
|Name (Nazwa)|Zasady bezpiecznych łączy dla wszystkich adresatów w domenie|
|Wybierz akcję dla nieznanych potencjalnie złośliwych adresów URL w komunikatach|Wybierz pozycję **Włączone — adresy URL zostaną ponownie zapisane i sprawdzone pod kątem listy znanych złośliwych linków po kliknięciu linku przez użytkownika**.|
|Stosowanie skanowania adresów URL w czasie rzeczywistym w poszukiwaniu podejrzanych linków i linków wskazujących pliki|Zaznacz to pole.|
|Zastosowane do|Domena adresata to . . . wybierz domenę.|

> [!TIP]
> Aby uzyskać więcej informacji, zobacz [Bezpieczne linki w Ochrona usługi Office 365 w usłudze Microsoft Defender](../../security/office-365-security/atp-safe-links.md).

## <a name="increase-protection-for-your-organizations-devices"></a>Zwiększanie ochrony urządzeń organizacji

Program antywirusowy Microsoft Defender jest wbudowany w system operacyjny Windows i zapewnia dobrą ochronę przed wirusami i złośliwym oprogramowaniem. Jednak możesz zwiększyć ochronę urządzeń organizacji, dołączając je do Microsoft Defender dla Firm, która jest nową ofertą dla małych i średnich firm, takich jak Twoja, i jest dołączona do [Microsoft 365 Business Premium](../../business-premium/index.md). Dzięki usłudze Defender dla Firm urządzenia organizacji są lepiej chronione przed oprogramowaniem wymuszającym okup, złośliwym oprogramowaniem, wyłudzaniem informacji i innymi zagrożeniami.

Dzięki Microsoft 365 Business Premium uzyskujesz zwiększone funkcje zabezpieczeń, takie jak zarządzanie urządzeniami i zaawansowana ochrona przed zagrożeniami. Podczas rejestrowania urządzeń w usłudze Microsoft 365 Business for Defender urządzenia są monitorowane i chronione przez usługę InTune.


Aby dowiedzieć się więcej, zobacz następujące zasoby:

- [Omówienie usługi Microsoft Defender dla Firm](../../security/defender-business/mdb-overview.md)

- [Konfigurowanie i konfigurowanie Microsoft Defender dla Firm](../../security/defender-business/mdb-setup-configuration.md)

- [Wprowadzenie do korzystania z portalu Microsoft 365 Defender](../../security/defender-business/mdb-get-started.md)

## <a name="related-content"></a>Zawartość pokrewna

[Uwierzytelnianie wieloskładnikowe dla platformy Microsoft 365](multi-factor-authentication-microsoft-365.md) (artykuł)\
[Zarządzanie kontami priorytetów i monitorowanie ich](../setup/priority-accounts.md) (artykuł)\
[Raporty platformy Microsoft 365 w centrum administracyjnym](../activity-reports/activity-reports.md) (wideo)\
[Microsoft 365 Business Premium — cyberbezpieczeństwo dla małych firm](/microsoft-365/business-premium/) (artykuł)\

