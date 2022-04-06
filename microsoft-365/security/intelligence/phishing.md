---
title: Jak chronić przed atakami wyłudzających informacje
ms.reviewer: ''
description: Dowiedz się, jak działa wyłudzanie informacji, dostarczaj do urządzeń złośliwe oprogramowanie i co możesz zrobić, aby się ochronić
keywords: zabezpieczenia, złośliwe oprogramowanie, wyłudzanie informacji, informacje, oszustwo, socjopcja, ochrona, ochrona, trendy, ataki kierowane
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
ms.openlocfilehash: 39b998b69b62a8c927ff26c1325d8a88812e0be6
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63706040"
---
# <a name="how-to-protect-against-phishing-attacks"></a>Jak chronić przed atakami wyłudzających informacje

Ataki służące do wyłudzania informacji próbują ukraść informacje poufne za pośrednictwem wiadomości e-mail, witryn internetowych, wiadomości SMS lub innych form komunikacji elektronicznej. Kontakty te wyglądają jak oficjalne wiadomości od legalnych firm lub osób.

Cyberprzestępcy często usiłują ukraść nazwy użytkowników, hasła, dane kart kredytowych, informacje o koncie bankowym lub inne poświadczenia. Używają one skradzionych informacji do celów złośliwych, takich jak włamanie się, kradzież tożsamości czy kradzież pieniędzy bezpośrednio z kont bankowych i kart kredytowych. Informacje te można również sprzedawać na rynkach cyberprzestępców.

Ataki ze społeczności są przeznaczone do korzystania z możliwości użytkownika poklatkowe w podejmowaniu decyzji. Nie podawać informacji poufnych ani osobistych za pośrednictwem poczty e-mail, nieznanych witryn internetowych lub przez telefon. Pamiętaj, że wiadomości e-mail służące do wyłudzania informacji wyglądają jak prawdziwe.

## <a name="learn-the-signs-of-a-phishing-scam"></a>Poznaj znaki wyłudzania informacji

Najlepszą ochroną jest świadomość i edukacja. Nie otwieraj załączników ani linków w niezamówionych wiadomościach e-mail, nawet jeśli pochodzą z rozpoznanego źródła. Jeśli wiadomość e-mail jest nieoczekiwana, nie należy otwierać załącznika i zweryfikować adres URL.

Przedsiębiorstwa powinny kształcić i przeszkolić pracowników w zakresie wszelkich komunikacji żądanych informacji osobistych lub finansowych. Powinni również poinstruować pracowników, aby natychmiast zgłaszali zagrożenie zespołowi ds. bezpieczeństwa w firmie.

Oto kilka oznak wyłudzania informacji:

* Linki lub adresy URL udostępniane w wiadomościach e-mail nie wskazują odpowiedniej lokalizacji ani nie wskazują witryny innej firmy, która nie jest powiązana z nadawcą wiadomości e-mail. Na przykład na obrazie poniżej podanego adresu URL nie odpowiada adresowi URL, do który zostanie wykonane.

    ![Przykład umieszczenia wskaźnika myszy na adresie URL.](../../media/security-intelligence-images/url-hover.png)

* Istnieje prośba **o dane osobowe** , takie jak numery PESEL, informacje bankowe lub finansowe. Oficjalna korespondencja zasadniczo nie poprosi Cię o informacje osobiste w formie wiadomości e-mail.

* **Elementy w adresie e-mail zostaną zmienione** , tak aby przypominały na tyle podobny do prawdziwego adresu e-mail, ale dodano cyfry lub zmieniono litery.

* Wiadomość jest **nieoczekiwana i niezamawiana**. Jeśli nagle otrzymasz wiadomość e-mail od jednostki lub osoby, której rzadko się zajmujesz, rozważ tę wiadomość e-mail podejrzaną.

* Ten komunikat lub załącznik zawiera prośbę o włączenie **makr, dostosowanie ustawień zabezpieczeń lub zainstalowanie aplikacji**. Normalne wiadomości e-mail nie będą chcieć tego robić.

* Komunikat zawiera **błędy**. Poprawne wiadomości firmowe mają mniejsze prawdopodobieństwo, że zawierają błędy typograficzne lub gramatyczne albo zawierają nieprawidłowe informacje.

* Adres **nadawcy nie odpowiada podpisowi** w samej wiadomości. Wiadomość e-mail rzekomo pochodzi z firmy Mary of Contoso Corp, ale adres nadawcy to jan<span></span>@example.com.

* W **polu "** Do" znajduje się wielu adresatów, którzy wyglądają jak losowe adresy. Wiadomości firmowe zazwyczaj są wysyłane bezpośrednio do poszczególnych adresatów.

* Pozdrowienie w samej wiadomości nie **ma dla Ciebie adresu osobistego**. Oprócz wiadomości, w których błędnie adresują się inne osoby, powitania, które błędnie wymuszają nazwę użytkownika lub ściągają je bezpośrednio z adresu e-mail, zwykle są złośliwe.

* Witryna internetowa wygląda znajomo, ale występują niespójności lub błędy **, które są nieprawidłowości**. Do znaków ostrzegawczych należą nieaktualne logo, literówki lub prośba użytkowników o poprosienie o dodatkowe informacje, o które użytkownik nie jest pytany w przypadku legalnych witryn logowania.

* Otwarta strona nie **jest stroną na żywo, a** raczej obrazem zaprojektowanym tak, aby wyglądał jak witryna, która jest znana Ci z pracy. Może zostać wyświetlone okno podręczne z prośbą o poświadczenia.

W razie wątpliwości skontaktuj się z firmą za pośrednictwem znanych kanałów, aby sprawdzić, czy podejrzane wiadomości e-mail są w rzeczywistości prawdziwe.

## <a name="software-solutions-for-organizations"></a>Rozwiązania programowe dla organizacji

* [Microsoft Edge](/microsoft-edge/deploy/index) i [Windows Defender Application Guard](/windows/security/microsoft-defender-application-guard/md-app-guard-overview.md) oferują ochronę przed coraz większymi zagrożeniami ukierunkowanych ataków przy użyciu wiodącej w branży technologii Hyper-V virtualization firmy Microsoft. Jeśli przeglądana witryna internetowa jest uważane za niezaufaną, kontener hyper-V odizoluje to urządzenie od reszty sieci, uniemożliwiając tym samym dostęp do danych przedsiębiorstwa.

* [Microsoft Exchange Online Protection (EOP)](https://products.office.com/exchange/exchange-email-security-spam-protection) zapewnia niezawodność klasy korporacyjnej oraz ochronę przed spamem i złośliwym oprogramowaniem przy zachowaniu dostępu do poczty e-mail w nagłych w sytuacjach awaryjnych i po ich zakończeniu.  Korzystając z różnych warstw filtrowania, program EOP może zapewniać różne kontrolki filtrowania spamu, takie jak kontrolki poczty masowej i spam międzynarodowy, co dodatkowo usprawnia usługi ochrony.

* Użyj [programu Microsoft Defender dla Office 365](https://products.office.com/exchange/online-email-threat-protection?ocid=cx-blog-mmpc) ochrony poczty e-mail, plików i magazynu online przed złośliwym oprogramowaniem. Zapewnia on ochronę treści w Microsoft Teams, Word, Excel, PowerPoint, Visio, SharePoint Online i OneDrive dla Firm. Zabezpieczając niebezpieczne załączniki i rozszerzając ochronę przed złośliwymi linkami, uzupełnia on funkcje zabezpieczeń programu Exchange Online Protection, aby zapewnić lepszą ochronę przez zero dni.

## <a name="what-to-do-if-youve-been-a-victim-of-a-phishing-scam"></a>Co zrobić, jeśli padłeś ofiarą próby wyłudzenia informacji

Jeśli uważasz, że jesteś ofiarą ataku, który ma na celu wyłudzanie informacji:

1. Skontaktuj się z administratorem IT, jeśli używasz komputera służbowego
2. Natychmiast zmień wszystkie hasła skojarzone z kontami
3. Zgłaszanie wszelkich nieuprawnianych działań firmie bankowej i karty kredytowej

### <a name="reporting-spam"></a>Zgłaszanie spamu

- **Outlook.com**: Jeśli otrzymasz podejrzaną wiadomość e-mail z prośbą o informacje osobiste, zaznacz pole wyboru obok tej wiadomości w Outlook odbiorczej. Wybierz strzałkę obok pozycji **Wiadomość-śmieć**, a następnie wybierz pozycję **Wyłudzanie informacji**.

- **Microsoft Office Outlook**: W podejrzanej wiadomości wybierz pozycję Zgłoś **wiadomość na** wstążce, a następnie wybierz pozycję Wyłudzanie **informacji**.

- **Microsoft 365**: Użyj portalu Przesyłanie w [programie Microsoft 365 Defender](/microsoft-365/security/office-365-security/report-junk-email-messages-to-microsoft), aby przesłać do firmy Microsoft próbkę wiadomości-śmieci lub próby wyłudzenia informacji w celu analizy. Aby uzyskać więcej informacji, zobacz [Zgłaszanie wiadomości i plików do firmy Microsoft](/microsoft-365/security/office-365-security/report-junk-email-messages-to-microsoft).

- **Grupa robocza ochrona przed wyłudzaniem** informacji: phishing-report@us-cert.gov. Grupa korzysta z raportów generowanych na podstawie wiadomości e-mail wysyłanych w celu zwalczania prób wyłudzania informacji i hakerów. W związku z tym są zaangażowani dostawcy usług internetowych, dostawcy zabezpieczeń, instytucje finansowe i instytucje porządkowe.

### <a name="if-youre-on-a-suspicious-website"></a>Jeśli używasz podejrzanej witryny internetowej

- **Microsoft Edge**: Będąc w podejrzanej witrynie, wybierz ikonę **Więcej (...)** >  Pomoc i opinieRaportuj >  **niebezpieczną witrynę**. Postępuj zgodnie z wyświetlanymi na niej instrukcjami, aby zgłosić witrynę.

- **Internet Explorer**: Gdy znajdujesz się w podejrzanej witrynie, wybierz ikonę koła zębatego, wskaż pozycję **Bezpieczeństwo, a** następnie wybierz pozycję Zgłoś niebezpieczną **witrynę internetową**. Postępuj zgodnie z wyświetlanymi na niej instrukcjami, aby zgłosić witrynę.

## <a name="more-information-about-phishing-attacks"></a>Więcej informacji o atakach wyłudzających informacje

- [Chroń się przed wyłudzaniem informacji](https://support.microsoft.com/help/4033787/windows-protect-yourself-from-phishing)
- [Trendy wyłudzania informacji](phishing-trends.md)
