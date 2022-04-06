---
title: Office 365 omówienie zabezpieczeń, Ochrona usługi Office 365 w usłudze Microsoft Defender, EOP, MSDO
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 08/13/2020
audience: Admin
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Zabezpieczenia w Office 365, od usługi EOP do Ochrona usługi Office 365 w usłudze Defender planów 1 i 2, konfiguracji standardowej i ścisłej konfiguracji zabezpieczeń i nie tylko. Dowiedz się, co masz, i dowiedz się, jak zabezpieczyć swoje właściwości.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d75ed9a3b01a7a16e283ce007f7c4a5b50cdab09
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467494"
---
# <a name="office-365-security"></a>Office 365 zabezpieczeń


**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 i plan 2](defender-for-office-365.md)


Ten artykuł zawiera wprowadzenie do nowych właściwości zabezpieczeń w chmurze. Niezależnie od tego, czy jesteś częścią Centrum operacji zabezpieczeń, jesteś administratorem zabezpieczeń w tym miejscu, czy chcesz odświeżyć swoją pracę.

> [!CAUTION]
> Jeśli korzystasz z usługi **Outlook.com**, **Microsoft 365 Family** lub **Microsoft 365 Personal** i potrzebujesz linków *Sejf* lub załączników programu *Sejf*, kliknij ten ***link***: Zaawansowane zabezpieczenia usługi [Outlook.com dla Microsoft 365 subskrybenci](https://support.microsoft.com/office/advanced-outlook-com-security-for-office-365-subscribers-882d2243-eab9-4545-a58a-b36fee4a46e2).

## <a name="office-365-security-spelled-out"></a>Office 365 o zabezpieczeniach

Każda Office 365 ma funkcje zabezpieczeń. Cele i działania, jakie możesz podjąć, zależą od fokusu tych różnych subskrypcji. W Office 365 zabezpieczeń istnieją trzy główne usługi zabezpieczeń (lub produkty) powiązane z typem subskrypcji:

1. Exchange Online Protection (EOP)
1. Ochrona usługi Office 365 w usłudze Microsoft Defender Plan 1 (Defender dla Office P1)
1. Ochrona usługi Office 365 w usłudze Microsoft Defender Plan 2 (Defender dla komputerów Office P2)

> [!NOTE]
> Jeśli zakupiono subskrypcję i chcesz teraz w tej chwili w programie zapewnić funkcje *zabezpieczeń, przejdź* do procedury opisanej w artykule Ochrona [przed zagrożeniami](protect-against-threats.md) . Jeśli dopiero zaczynasz korzystać z subskrypcji i chcesz poznać swoją licencję przed rozpoczęciem, przejrzyj strony Rozliczenia > Produkty w [Centrum administracyjne platformy Microsoft 365.](https://admin.microsoft.com/AdminPortal/#/homepage)

Office 365 zabezpieczeń na podstawie podstawowych zabezpieczeń oferowanych przez usługę EOP. Usługa EOP jest obecna w dowolnej subskrypcji, Exchange Online można znaleźć skrzynki pocztowe (pamiętaj, że wszystkie produkty zabezpieczające omówione tutaj są oparte na chmurze).

Być może wiesz, że te trzy składniki zostały omówione w ten sposób:

|EOP|Ochrona usługi Office 365 w usłudze Microsoft Defender P1|Ochrona usługi Office 365 w usłudze Microsoft Defender P2|
|---|---|---|
|Zapobiega szerokiemu, znanemu atakowi opartemu na woluminie.|Chroni pocztę e-mail i współpracę przed złośliwym oprogramowaniem, wyłudami i firmowymi zabezpieczeniami poczty e-mail.|Dodaje badania po naruszeniu, łowiectwo i reakcję, a także automatyzację i symulacyjne (na szkoleniach).|

Pod względem architektury zacznijmy jednak od pojęcia każdej z nich jako skumulowanych warstw zabezpieczeń z wyróżnieniem zabezpieczeń. Bardziej przypomina to:

<!--:::image type="content" source="../../media/tp-EOPATPStack.PNG" alt-text="Placeholder graphic.":::-->

:::image type="content" source="../../media/tp_GraphicEOPATPP1P2_2.png" alt-text="Usługi EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender oraz ich relacje między sobą z wyróżnieniem usługi, w tym notatką do uwierzytelniania pocztą e-mail" lightbox="../../media/tp_GraphicEOPATPP1P2_2.png":::

Mimo że każda z tych usług ma na celu ochrona, wykrywanie, badanie i odpowiadanie, ***wszystkie** _ usługi mogą wykonywać _ *_dowolne_** cele ochrony, wykrywania, badania i odpowiadania.

Podstawową zasadą Office 365 jest ochrona EOP. Ochrona usługi Office 365 w usłudze Microsoft Defender P1 zawiera program EOP. Ochrona usługi Office 365 w usłudze Defender P2 zawiera składniki P1 i EOP. Struktura jest skumulowana. Dlatego podczas konfigurowania tego produktu należy uruchomić usługę EOP i pracować nad jej Ochrona usługi Office 365 w usłudze Defender.

Konfiguracja uwierzytelniania wiadomości e-mail odbywa się w publicznym systemie DNS, jednak warto skonfigurować tę funkcję, aby ułatwić obronę przed fałszercą. *Jeśli masz usługę EOP,* ***musisz skonfigurować [uwierzytelnianie poczty e-mail](email-validation-and-authentication.md)***.

Jeśli masz konto Office 365 E3 lub poniżej, masz usługę EOP, ale z opcją zakupu autonomicznego Ochrona usługi Office 365 w usłudze Defender P1 przez uaktualnienie. Jeśli masz Office 365 E5, masz już Ochrona usługi Office 365 w usłudze Defender P2.

> [!TIP]
> Jeśli Twoja subskrypcja nie jest Office 365 E3 ani E5, możesz sprawdzić, czy masz możliwość uaktualnienia do Ochrona usługi Office 365 w usłudze Microsoft Defender P1. Jeśli chcesz, ta strona sieci [](https://www.microsoft.com/microsoft-365/exchange/advance-threat-protection#coreui-contentrichblock-x07wids) Web zawiera listę subskrypcji, które można uaktualnić do Ochrona usługi Office 365 w usłudze Microsoft Defender P1 (sprawdź, czy na końcu strony jest drobnym drukiem).

## <a name="the-office-365-security-ladder-from-eop-to-microsoft-defender-for-office-365"></a>Ten Office 365 zabezpieczeń od EOP do Ochrona usługi Office 365 w usłudze Microsoft Defender

![Program EOP Ochrona usługi Office 365 w usłudze Microsoft Defender oraz ich wyróżnienia w zakresie zabezpieczeń, przechodząc z chroń i wykryj, aby zbadać i odpowiedzieć. Konfiguracja uwierzytelniania poczty e-mail (co najmniej DKIM i DMARC) powinna zostać skonfigurowania dla usługi EOP i konfiguracji.](../../media/tp_EOPATPP1P2Take6.gif#lightbox)

> [!IMPORTANT]
> Zapoznaj się ze szczegółami na tych [stronach: Exchange Online Protection](exchange-online-protection-overview.md) i [Ochrona usługi Office 365 w usłudze Defender](defender-for-office-365.md).

To, co sprawia Ochrona usługi Office 365 w usłudze Microsoft Defender dodanie planów korzyści wyłącznie z zarządzania zagrożeniami WOOP może być trudne do odsłoniania na pierwszy rzut oka. Aby ułatwić sortowanie, czy ścieżka uaktualnienia jest właściwa dla Twojej organizacji, przyjrzyjmy się możliwościom poszczególnych produktów, jeśli chodzi o:

- zapobieganie i wykrywanie zagrożeń
- badanie
- odpowiadanie

zaczynając od **Exchange Online Protection**:
<p>

|Zapobieganie/wykrywanie|Zbadaj|Odpowiadanie|
|---|---|---|
|Do technologii należą:<ul><li>spam</li><li>phish</li><li>złośliwe oprogramowanie</li><li>poczta masowa</li><li>fałszywa inteligencja</li><li>wykrywanie personifikacji</li><li>Kwarantanna administratora</li><li>Przesyłanie przez administratora i użytkownika wyników wyników fałszywie dodatnich i wyników fałszywie ujemnych</li><li>Zezwalaj na/blokuj dla adresów URL i plików</li><li>Raporty</li></ul>|<li>Przeszukiwanie dziennika inspekcji</li><li>Śledzenie wiadomości</li>|<li>Automatyczne czyszczenie zerowej godziny (ZAP)</li><li>Uściślij i testuj listy zezwalania i blokowania</li>|

Jeśli chcesz przejść do programu EOP, przejdź **[do tego artykułu](exchange-online-protection-overview.md)**.

Ponieważ te produkty mają charakter skumulowany, Ochrona usługi Office 365 w usłudze Microsoft Defender P1 i zdecydujesz się go subskrybować, dodasz te możliwości.

Zyski z **Ochrona usługi Office 365 w usłudze Defender, Plan 1** (do tej pory):
<p>

|Zapobieganie/wykrywanie|Zbadaj|Odpowiadanie|
|---|---|---|
|Technologie obejmują wszystko w UOP oraz:<ul><li>Sejf załączników</li><li>Sejf linków<li>Ochrona usługi Office 365 w usłudze Microsoft Defender ochrony obciążeń (np. SharePoint online, Teams, OneDrive dla Firm)</li><li>Ochrona poczty e-mail, poczty e-mail, Office klientów i klientów Teams</li><li>ochrona przed wyłudzaniem informacji w programie Ochrona usługi Office 365 w usłudze Defender</li><li>Ochrona użytkownika i personifikacji domeny</li><li>Alerty i interfejs API integracji interfejsu SIEM dla alertów</li>|<li>Interfejs API integracji SIEM do wykrywania</li><li>**Narzędzie do wykrywania w czasie rzeczywistym**</li><li>Śledzenie adresu URL</li>|<li>Takie same</li></ul>

Dlatego Ochrona usługi Office 365 w usłudze Microsoft Defender P1 zostanie rozszerzony na stronę *prevention_of the **house** i doda dodatkowe formy _*_detection_**.

Ochrona usługi Office 365 w usłudze Microsoft Defender P1 dodaje również **wykrywanie w** czasie rzeczywistym dla badań. To narzędzie do ochrony przed zagrożeniami jest pogrubione, ponieważ dzięki temu wiadomo,  że Ochrona usługi Office 365 w usłudze Defender P1. Nie jest ona wyświetlana na Ochrona usługi Office 365 w usłudze Defender P2.

Zyski z **Ochrona usługi Office 365 w usłudze Defender, Plan 2** (do tej pory):
<p>

|Zapobieganie/wykrywanie|Zbadaj|Odpowiadanie|
|---|---|---|
|Technologie obejmują wszystko w UOKI, a Ochrona usługi Office 365 w usłudze Microsoft Defender P1 oraz:<ul><li>Takie same</li>|<li>**Eksplorator zagrożeń**</li><li>Moduły śledzące zagrożenia</li><li>Widoki kampanii</li>|<li>Zautomatyzowane badania i odpowiedzi (AIR)</li><li>AIR z Eksploratora zagrożeń</li><li>AIR w przypadku naruszonych użytkowników</li><li>Interfejs API integracji usług SIEM dla zautomatyzowanych badań</li>

Dlatego Ochrona usługi Office 365 w usłudze Microsoft Defender P2 rozszerza się po stronie badania i odpowiedzi domu  i dodaje nową siłę łętwną. Automatyzacja.

W Ochrona usługi Office 365 w usłudze Microsoft Defender P2 główne narzędzie wyszukiwania jest nazywane Eksploratorem **zagrożeń, a** nie wykrywaniem w czasie rzeczywistym. Jeśli zobaczysz Eksplorator zagrożeń, gdy przechodzisz do Defender dla Chmury, jesteś na Ochrona usługi Office 365 w usłudze Microsoft Defender P2.

Aby przejść do szczegółów Ochrona usługi Office 365 w usłudze Microsoft Defender P1 i P2, **[przejdź do tego artykułu](defender-for-office-365.md)**.

> [!TIP]
> EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender także różnią się w przypadku użytkowników końcowych. W usługach EOP i Ochrona usługi Office 365 w usłudze Defender P1 fokus znajduje się na *informacji,* dlatego te dwie usługi dodają komunikat Report Outlook (Raport), który umożliwia użytkownikom zgłaszanie wiadomości *e-mail*, które znajdą podejrzanie, w celu dalszej analizy. <p> W Ochrona usługi Office 365 w usłudze Defender P2 (który zawiera wszystko w usługach EOP i P1) fokus przesunie się  na dalsze szkolenia dla użytkowników końcowych, dzięki czemu Centrum operacji zabezpieczeń będzie mieć dostęp do zaawansowanego  narzędzia skupu się na zagrożeniach i jego metryk dla użytkowników końcowych.

## <a name="microsoft-defender-for-office-365-plan-1-vs-plan-2-cheat-sheet"></a>Ochrona usługi Office 365 w usłudze Microsoft Defender Plan 1 a Plan 2 - ściągawka

Ten podręczny przewodnik pomoże Ci zrozumieć, jakie funkcje są dostępne w ramach poszczególnych Ochrona usługi Office 365 w usłudze Microsoft Defender subskrypcji. W połączeniu z Twoją wiedzą na temat funkcji usługi EOP może ona pomóc twórcom biznesowym w określeniu, Ochrona usługi Office 365 w usłudze Microsoft Defender jest najlepszy dla ich potrzeb.

|Ochrona usługi Office 365 w usłudze Defender Plan 1|Ochrona usługi Office 365 w usłudze Defender Plan 2|
|---|---|
|Funkcje konfiguracji, ochrony i wykrywania: <ul><li>[Sejf załączników](safe-attachments.md)</li><li>[Bezpieczne linki](safe-links.md)</li><li>[Sejf załączników do SharePoint, OneDrive i Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[Ochrona przed wyłudzaniem informacji w programie Ochrona usługi Office 365 w usłudze Defender](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[Wykrywanie w czasie rzeczywistym](threat-explorer.md)</li></ul>|Ochrona usługi Office 365 w usłudze Defender funkcji Plan 1 <p> --- plus --- <p> Funkcje automatyzacji, badań, rozwiązywania problemów i edukacji: <ul><li>[Moduły śledzące zagrożenia](threat-trackers.md)</li><li>[Eksplorator zagrożeń](threat-explorer.md)</li><li>[Zautomatyzowane badanie i reagowanie](office-365-air.md)</li><li>[Atak zbędny](attack-simulator.md)</li></ul>|

- Ochrona usługi Office 365 w usłudze Microsoft Defender Plan 2 jest zawarty w Office 365 E5, Office 365 A5 i Microsoft 365 E5.

- Ochrona usługi Office 365 w usłudze Microsoft Defender Plan 1 jest dołączony do Microsoft 365 Business Premium.

- Ochrona usługi Office 365 w usłudze Microsoft Defender Plan 1 i Ochrona usługi Office 365 w usłudze Defender Plan 2 są dostępne jako dodatek dla niektórych subskrypcji. Aby dowiedzieć się więcej, oto kolejny link Dostępność funkcji w [Ochrona usługi Office 365 w usłudze Microsoft Defender planów](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

- Funkcja [Sejf dokumenty](safe-docs.md) jest dostępna tylko dla użytkowników z licencjami Microsoft 365 E5 lub Zabezpieczenia platformy Microsoft 365 E5 (nieujętą w Ochrona usługi Office 365 w usłudze Microsoft Defender).

- Jeśli Twoja bieżąca subskrypcja nie zawiera Ochrona usługi Office 365 w usłudze Microsoft Defender i chcesz, skontaktuj się ze sprzedażą, aby rozpocząć okres próbny, [i](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html) dowiedz się, Ochrona usługi Office 365 w usłudze Microsoft Defender w Twojej organizacji.

> [!TIP]
> ***Porada niejawnego programu** testów. Za pomocą spisu docs.microsoft.com można uzyskać informacje na temat programu EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender. Wróć do tej strony, [Office 365 omówienie](index.yml) zabezpieczeń, a na pasku bocznym zauważysz, że organizacja spisu treści jest organizacją. Proces ten rozpoczyna się od wdrożenia (w tym migracji), a następnie jest w dalszym ciągu zapobieganie, wykrywanie, badanie i reagowanie. <p> Ta struktura jest podzielona, tak aby po tematach _ *Security Administration** były **poruszane tematy dotyczące operacji zabezpieczeń** . Jeśli jesteś nowym członkiem zespołu na stanowisku, skorzystaj z linku zawartego w tej poradce i swojej wiedzy na temat spisu treści, aby dowiedzieć się więcej na ten temat. Pamiętaj, aby na *czas korzystać z linków opinii* i *oceniać* artykuły. Opinie pomagają nam ulepszać to, co oferujemy.

## <a name="where-to-go-next"></a>Gdzie przejść dalej

Jeśli jesteś administratorem zabezpieczeń, może być konieczne skonfigurowanie DKIM lub DMARC dla poczty. Możesz chcieć, aby dla użytkowników priorytetowych było publikowane "Ścisłe" ustawienia wstępne zabezpieczeń, lub poszukać nowych nowości w tym produkcie. Jeśli natomiast korzystasz z usługi Security Ops, możesz chcieć korzystać z wykrywania w czasie rzeczywistym lub Eksploratora zagrożeń w celu zbadania i reakcji albo przeprowadzić wykrywanie użytkowników końcowych za pomocą ataku i odpowiedzi. Tak czy inaczej, poniżej poszło kilka dodatkowych zaleceń, które należy sprawdzić w następnych krokach.

[Uwierzytelnianie poczty e-mail, w tym SPF, DKIM i DMARC (z linkami do konfiguracji wszystkich trzech)](email-validation-and-authentication.md)

[Zapoznaj się z zalecanymi "złotymi" konfiguracjami](recommended-settings-for-eop-and-office365.md) i użyj ich zalecanych ustawień wstępnych, [aby szybko skonfigurować zasady zabezpieczeń](preset-security-policies.md)

Na bieżąco z [nowościami w programie Ochrona usługi Office 365 w usłudze Microsoft Defender (w tym nad rozwojem programu EOP)](whats-new-in-defender-for-office-365.md)

[Korzystanie z wykrywania w Eksploratorze zagrożeń lub w czasie rzeczywistym](threat-explorer.md)

Używanie [funkcji Ataków w programie Ochrona usługi Office 365 w usłudze Microsoft Defender](attack-simulator.md)
