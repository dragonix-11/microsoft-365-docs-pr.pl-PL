---
title: Jak chronić przed atakami wyłudzania informacji
ms.reviewer: ''
description: Dowiedz się, jak działa wyłudzanie informacji, dostarczać złośliwe oprogramowanie do swoich urządzeń i co możesz zrobić, aby się chronić
keywords: zabezpieczenia, złośliwe oprogramowanie, wyłudzanie informacji, oszustwo, inżynieria społeczna, przynęta, przynęta, ochrona, trendy, atak ukierunkowany
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: 1f414c80d3c0b5478112cd402f8e3839908787d4
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666773"
---
# <a name="how-to-protect-against-phishing-attacks"></a>Jak chronić przed atakami wyłudzania informacji

Ataki wyłudzające informacje próbują wykraść poufne informacje za pośrednictwem wiadomości e-mail, witryn internetowych, wiadomości tekstowych lub innych form komunikacji elektronicznej. Starają się wyglądać jak oficjalna komunikacja od legalnych firm lub osób fizycznych.

Cyberprzestępcy często próbują ukraść nazwy użytkownika, hasła, dane karty kredytowej, informacje o koncie bankowym lub inne poświadczenia. Wykorzystują skradzione informacje do złośliwych celów, takich jak hakowanie, kradzież tożsamości lub kradzież pieniędzy bezpośrednio z kont bankowych i kart kredytowych. Informacje te mogą być również sprzedawane na podziemnych rynkach cyberprzestępców.

Ataki inżynierii społecznej mają na celu wykorzystanie możliwości użytkownika w podejmowaniu decyzji. Bądź świadomy i nigdy nie podaj informacji poufnych lub osobistych za pośrednictwem poczty e-mail lub nieznanych witryn internetowych lub przez telefon. Pamiętaj, że wiadomości e-mail wyłudzające informacje są zaprojektowane tak, aby były uzasadnione.

## <a name="learn-the-signs-of-a-phishing-scam"></a>Poznaj oznaki oszustwa polegającego na wyłudzaniu informacji

Najlepszą ochroną jest świadomość i edukacja. Nie otwieraj załączników ani linków w niechcianych wiadomościach e-mail, nawet jeśli wiadomości e-mail pochodzą z rozpoznanego źródła. Jeśli wiadomość e-mail jest nieoczekiwana, należy uważać na otwarcie załącznika i zweryfikowanie adresu URL.

Przedsiębiorstwa powinny edukować i szkolić swoich pracowników, aby uważali na wszelkie komunikaty, które żądają informacji osobistych lub finansowych. Powinni oni również poinstruować pracowników, aby natychmiast zgłosili zagrożenie zespołowi ds. operacji zabezpieczeń firmy.

Oto kilka oznak wyłudzania informacji:

* Linki lub adresy URL podane w wiadomościach e-mail **nie wskazują prawidłowej lokalizacji** lub wskazują witrynę innej firmy, która nie jest powiązana z nadawcą wiadomości e-mail. Na przykład na poniższej ilustracji podany adres URL nie jest zgodny z adresem URL, do który zostanie wyświetlony.

    ![przykład umieszczenia wskaźnika myszy nad adresem URL.](../../media/security-intelligence-images/url-hover.png)

* Istnieje **prośba o dane osobowe** , takie jak numery ubezpieczenia społecznego lub informacje bankowe lub finansowe. Oficjalna komunikacja zwykle nie będzie żądać od Ciebie danych osobowych w formie wiadomości e-mail.

* **Elementy na adresie e-mail zostaną zmienione** tak, aby były wystarczająco podobne do prawidłowego adresu e-mail, ale dodały cyfry lub zmienione litery.

* Wiadomość jest **nieoczekiwana i niechciana**. Jeśli nagle otrzymasz wiadomość e-mail od jednostki lub osoby, z którą rzadko masz do czynienia, rozważ to podejrzane wiadomości e-mail.

* Komunikat lub załącznik z prośbą o **włączenie makr, dostosowanie ustawień zabezpieczeń lub zainstalowanie aplikacji**. Zwykłe wiadomości e-mail nie będą cię o to prosić.

* Komunikat zawiera **błędy**. Uzasadnione komunikaty firmowe są mniej narażone na błędy typograficzne lub gramatyczne lub zawierają nieprawidłowe informacje.

* **Adres nadawcy nie jest zgodny z podpisem** samej wiadomości. Na przykład wiadomość e-mail jest rzekomo od Mary z Contoso Corp, ale adres nadawcy to john<span></span>@example.com.

* W polu "Do" znajduje się **wielu adresatów** , którzy wydają się być adresami losowymi. Komunikaty firmowe są zwykle wysyłane bezpośrednio do poszczególnych adresatów.

* Powitanie samej wiadomości **nie zwraca się do Ciebie osobiście**. Oprócz wiadomości, które omyłkowo odnoszą się do innej osoby, pozdrowienia, które nadużywają Twojego imienia i nazwiska lub ściągają twoje imię i nazwisko bezpośrednio z adresu e-mail, wydają się być złośliwe.

* Witryna wygląda znajomo, ale istnieją **niespójności lub rzeczy, które nie są w porządku**. Znaki ostrzegawcze obejmują nieaktualne logo, literówki lub poproś użytkowników o podanie dodatkowych informacji, które nie są monitowane przez uzasadnione witryny logowania.

* Otwarta strona nie jest **stroną na żywo**, ale raczej obrazem zaprojektowanym tak, aby wyglądała jak witryna, którą znasz. Może zostać wyświetlone okno podręczne, które żąda poświadczeń.

W razie wątpliwości skontaktuj się z firmą za pomocą znanych kanałów, aby sprawdzić, czy jakiekolwiek podejrzane wiadomości e-mail są w rzeczywistości uzasadnione.

## <a name="software-solutions-for-organizations"></a>Rozwiązania programowe dla organizacji

* [Microsoft Edge](/microsoft-edge/deploy/index) i [Windows Defender Application Guard](/windows/security/microsoft-defender-application-guard/md-app-guard-overview.md) zapewniają ochronę przed rosnącym zagrożeniem ukierunkowanymi atakami przy użyciu wiodącej w branży technologii wirtualizacji funkcji Hyper-V firmy Microsoft. Jeśli przeglądana witryna internetowa zostanie uznana za niezaufaną, kontener funkcji Hyper-V odizoluje to urządzenie od pozostałej części sieci, uniemożliwiając dostęp do danych przedsiębiorstwa.

* [Microsoft Exchange Online Protection (EOP)](https://products.office.com/exchange/exchange-email-security-spam-protection) oferuje niezawodność klasy korporacyjnej i ochronę przed spamem i złośliwym oprogramowaniem, zachowując jednocześnie dostęp do poczty e-mail w nagłych wypadkach i po nich.  Korzystając z różnych warstw filtrowania, funkcja EOP może udostępniać różne mechanizmy kontroli filtrowania spamu, takie jak zbiorcze kontrole poczty e-mail i spam międzynarodowy, co jeszcze bardziej usprawni usługi ochrony.

* Użyj [Ochrona usługi Office 365 w usłudze Microsoft Defender](https://products.office.com/exchange/online-email-threat-protection?ocid=cx-blog-mmpc), aby chronić pocztę e-mail, pliki i magazyn online przed złośliwym oprogramowaniem. Oferuje ona holistyczną ochronę w usługach Microsoft Teams, Word, Excel, PowerPoint, Visio, SharePoint Online i OneDrive dla Firm. Ochrona przed niebezpiecznymi załącznikami i rozszerzanie ochrony przed złośliwymi linkami uzupełnia funkcje zabezpieczeń Exchange Online Protection w celu zapewnienia lepszej ochrony zero-day.

## <a name="what-to-do-if-youve-been-a-victim-of-a-phishing-scam"></a>Co zrobić, jeśli padłeś ofiarą oszustwa polegającego na wyłudzaniu informacji

Jeśli uważasz, że padłeś ofiarą ataku wyłudzania informacji:

1. Skontaktuj się z administratorem IT, jeśli jesteś na komputerze służbowym
2. Natychmiast zmień wszystkie hasła skojarzone z kontami
3. Zgłaszanie wszelkich fałszywych działań bankowi i firmie zajmującej się kartami kredytowymi

### <a name="reporting-spam"></a>Zgłaszanie spamu

- **Outlook.com**: Jeśli otrzymasz podejrzaną wiadomość e-mail z prośbą o podanie danych osobowych, zaznacz pole wyboru obok wiadomości w skrzynce odbiorczej Outlook. Wybierz strzałkę obok pozycji **Śmieci**, a następnie wybierz pozycję **Wyłudzanie informacji**.

- **Microsoft Office Outlook**: w podejrzanej wiadomości wybierz pozycję **Komunikat raportu** na wstążce, a następnie wybierz pozycję **Wyłudzanie informacji**.

- **Microsoft 365**: użyj [portalu Przesyłania w Microsoft 365 Defender](/microsoft-365/security/office-365-security/report-junk-email-messages-to-microsoft), aby przesłać przykład wiadomości-śmieci lub wyłudzanie informacji do firmy Microsoft w celu analizy. Aby uzyskać więcej informacji, zobacz [Zgłaszanie komunikatów i plików do firmy Microsoft](/microsoft-365/security/office-365-security/report-junk-email-messages-to-microsoft).

- **Grupa robocza chroniąca przed wyłudzaniem informacji**: phishing-report@us-cert.gov. Grupa używa raportów generowanych z wiadomości e-mail wysyłanych do walki z oszustwami phishingowymi i hakerami. Zaangażowani są dostawcy usług internetowych, dostawcy zabezpieczeń, instytucje finansowe i organy ścigania.

### <a name="if-youre-on-a-suspicious-website"></a>Jeśli korzystasz z podejrzanej witryny internetowej

- **Microsoft Edge**: Gdy jesteś w podejrzanej witrynie, wybierz **ikonę** >  Więcej (...)**Pomoc i opinieRaportuj** >  **niebezpieczną witrynę**. Postępuj zgodnie z instrukcjami wyświetlanymi na stronie internetowej, aby zgłosić witrynę internetową.

- **Internet Explorer**: gdy jesteś w podejrzanej witrynie, wybierz ikonę koła zębatego, wskaż pozycję **Bezpieczeństwo**, a następnie wybierz pozycję **Zgłoś niebezpieczną witrynę internetową**. Postępuj zgodnie z instrukcjami wyświetlanymi na stronie internetowej, aby zgłosić witrynę internetową.

## <a name="more-information-about-phishing-attacks"></a>Więcej informacji na temat ataków wyłudzania informacji

- [Ochrona przed wyłudzaniem informacji](https://support.microsoft.com/help/4033787/windows-protect-yourself-from-phishing)
- [Trendy wyłudzania informacji](phishing-trends.md)
