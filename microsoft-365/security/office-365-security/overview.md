---
title: Office 365 zabezpieczeń, w tym program Microsoft Defender dla Office 365 i Exchange Online Protection
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 07/21/2021
audience: Admin
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Zabezpieczenia w Office 365, od usługi EOP do programu Defender Office 365 planów 1 i 2, konfiguracji standardowej i ścisłej konfiguracji zabezpieczeń i nie tylko. Dowiedz się, co masz i jak zabezpieczyć swoje właściwości.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 20bb1dcf9c34f0f7507d8fec7c9025de03461533
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63317027"
---
# <a name="microsoft-defender-for-office-365-security-overview"></a>Omówienie zabezpieczeń Office 365 Microsoft Defender

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)

Ten artykuł zawiera wprowadzenie do nowej usługi Microsoft Defender dla Office 365 zabezpieczeń w chmurze. Niezależnie od tego, czy jesteś częścią Centrum operacji zabezpieczeń, jesteś administratorem zabezpieczeń w tym miejscu, czy chcesz odświeżyć swoją pracę.

> [!CAUTION]
> Jeśli korzystasz z usługi **Outlook.com**, **Microsoft 365 Family** lub **Microsoft 365 Personal** i potrzebujesz linków *Sejf* lub załączników programu *Sejf*, kliknij ten ***link***: Zaawansowane zabezpieczenia usługi [Outlook.com dla Microsoft 365 subskrybenci](https://support.microsoft.com/office/advanced-outlook-com-security-for-office-365-subscribers-882d2243-eab9-4545-a58a-b36fee4a46e2).

## <a name="what-is-defender-for-office-365-security"></a>Co to jest defender w Office 365 zabezpieczeń

Każda Office 365 ma funkcje zabezpieczeń. Cele i działania, jakie możesz podjąć, zależą od fokusu tych różnych subskrypcji. W Office 365 zabezpieczeń istnieją trzy główne usługi zabezpieczeń (lub produkty) powiązane z typem subskrypcji:

1. Exchange Online Protection (EOP)
1. Microsoft Defender for Office 365 Plan 1 (Defender for Office P1)
1. Microsoft Defender for Office 365 Plan 2 (Defender for Office P2)

> [!NOTE]
> Jeśli zakupiono subskrypcję i chcesz teraz w tej chwili w programie zapewnić funkcje *zabezpieczeń, przejdź* do procedury opisanej w artykule Ochrona [przed zagrożeniami](protect-against-threats.md) . Jeśli dopiero zaczynasz korzystać z subskrypcji i chcesz poznać swoją licencję przed rozpoczęciem, przejdź do strony Rozliczenia > Produkty w [centrum administracyjne platformy Microsoft 365.](https://admin.microsoft.com/AdminPortal/#/homepage)

Office 365 zabezpieczeń na podstawie podstawowych zabezpieczeń oferowanych przez usługę EOP. Usługa EOP jest obecna w dowolnej subskrypcji, Exchange Online można znaleźć skrzynki pocztowe (pamiętaj, że wszystkie produkty zabezpieczające omówione tutaj są oparte na chmurze).

Być może wiesz, że te trzy składniki zostały omówione w ten sposób:

|EOP|Microsoft Defender dla Office 365 P1|Microsoft Defender dla Office 365 P2|
|---|---|---|
|Zapobiega szerokiemu, znanemu atakowi opartemu na woluminie.|Chroni pocztę e-mail i współpracę przed złośliwym oprogramowaniem, wyłudami i firmowymi zabezpieczeniami poczty e-mail.|Dodaje badania po naruszeniu, łowiectwo i reakcję, a także automatyzację i symulacyjne (na szkoleniach).|
|

Pod względem architektury zacznijmy jednak od pojęcia każdej z nich jako skumulowanych warstw zabezpieczeń z wyróżnieniem zabezpieczeń. Bardziej przypomina to:

:::image type="content" source="../../media/tp_GraphicEOPATPP1P2_2.png" alt-text="Usługi EOP i Microsoft Defender Office 365 i ich relacje między sobą, dzięki wyróżnieniu usługi, w tym uwaga do uwierzytelniania pocztą e-mail.":::

Mimo że każda z tych usług ma na celu ochrona, wykrywanie, badanie i odpowiadanie, ***wszystkie** _ usługi mogą wykonywać _ *_dowolne_** cele ochrony, wykrywania, badania i odpowiadania.

Podstawową zasadą Office 365 jest ochrona EOP. Program Microsoft Defender for Office 365 P1 zawiera usługę EOP. Defender for Office 365 P2 contains P1 and EOP. Struktura jest skumulowana. Dlatego podczas konfigurowania tego produktu należy zacząć od usługi EOP i pracować z usługą Defender dla Office 365.

Konfiguracja uwierzytelniania wiadomości e-mail odbywa się w publicznym systemie DNS, jednak warto skonfigurować tę funkcję, aby ułatwić obronę przed fałszercą. *Jeśli masz usługę EOP,* ***musisz skonfigurować [uwierzytelnianie poczty e-mail](email-validation-and-authentication.md)***.

Jeśli masz program Office 365 E3 lub poniżej, masz usługę EOP, ale z opcją zakupu autonomicznego programu Defender dla systemu Office 365 P1 przez uaktualnienie. Jeśli masz już Office 365 E5, masz już defender dla Office 365 P2.

> [!TIP]
> Jeśli Twoja subskrypcja nie jest Office 365 E3 ani E5, możesz sprawdzić, czy masz możliwość uaktualnienia do programu Microsoft Defender dla systemu Office 365 P1. Jeśli chcesz, ta strona sieci [](https://www.microsoft.com/microsoft-365/exchange/advance-threat-protection#coreui-contentrichblock-x07wids) Web zawiera listę subskrypcji, które uprawniają do uaktualnienia programu Microsoft Defender for Office 365 P1 (sprawdź na końcu strony, aby uzyskać drobny wydruk).

## <a name="the-office-365-security-ladder-from-eop-to-microsoft-defender-for-office-365"></a>Zabezpieczenia Office 365 usługi EOP do programu Microsoft Defender dla Office 365

> [!IMPORTANT]
> Zapoznaj się ze szczegółami na tych [stronach: Exchange Online Protection](exchange-online-protection-overview.md) i [Defender for Office 365](defender-for-office-365.md).

Co sprawia, że dodanie programu Microsoft Defender dla programu Office 365 może być trudne do odsłoniania korzyści z zarządzania zagrożeniami wyłącznie za pomocą usługi EOP. Aby ułatwić sortowanie, czy ścieżka uaktualnienia jest właściwa dla Twojej organizacji, przyjrzyjmy się możliwościom poszczególnych produktów, jeśli chodzi o:

- zapobieganie i wykrywanie zagrożeń
- badanie
- odpowiadanie

zaczynając od **Exchange Online Protection**:
<p>

|Zapobieganie/wykrywanie|Badanie|Odpowiadanie|
|---|---|---|
|Do technologii należą:<ul><li>spam</li><li>phish</li><li>złośliwe oprogramowanie</li><li>poczta masowa</li><li>fałszywa inteligencja</li><li>wykrywanie personifikacji</li><li>Kwarantanna administratora</li><li>Przesyłanie przez administratora i użytkownika wyników wyników fałszywie dodatnich i wyników fałszywie ujemnych</li><li>Zezwalaj na/blokuj dla adresów URL i plików</li><li>Raporty</li></ul>|<li>Przeszukiwanie dziennika inspekcji</li><li>Śledzenie wiadomości</li>|<li>Automatyczne czyszczenie zerowej godziny (ZAP)</li><li>Uściślij i testuj listy zezwalania i blokowania</li>|
|

Jeśli chcesz przejść do programu EOP, przejdź **[do tego artykułu](exchange-online-protection-overview.md)**.

Ponieważ te produkty mają charakter skumulowany, jeśli oceniasz usługę Microsoft Defender dla programu Office 365 P1 i chcesz ją subskrybować, musisz dodać te możliwości.

Zyski z **defenderem dla Office 365, plan 1** (do tej pory):
<p>

|Zapobieganie/wykrywanie|Badanie|Odpowiadanie|
|---|---|---|
|Technologie obejmują wszystko w UOP oraz:<ul><li>Sejf załączników</li><li>Sejf linków<li>Usługa Microsoft Defender Office 365 ochrony obciążeń (np. SharePoint online, Teams, OneDrive dla Firm)</li><li>Ochrona poczty e-mail, poczty e-mail, Office klientów i klientów Teams</li><li>anti-phishing in Defender for Office 365</li><li>Ochrona użytkownika i personifikacji domeny</li><li>Alerty i interfejs API integracji interfejsu SIEM dla alertów</li>|<li>Interfejs API integracji SIEM do wykrywania</li><li>**Narzędzie do wykrywania w czasie rzeczywistym**</li><li>Śledzenie adresu URL</li>|<li>Takie same</li></ul>

Dlatego program Microsoft Defender dla Office 365 P1 rozszerza się po stronie ***prevention** _ domu i dodaje dodatkowe formy _*_detection_**.

Usługa Microsoft Defender dla Office 365 P1 dodaje również **wykrywanie** w czasie rzeczywistym na badaniach. To narzędzie do ochrony przed zagrożeniami jest pogrubione, ponieważ wiadomo, że masz  program Defender dla Office 365 P1. Nie jest ona wyświetlana w programie Defender Office 365 P2.

Zyski z **defenderem dla Office 365, plan 2** (do tej pory):
<p>

|Zapobieganie/wykrywanie|Badanie|Odpowiadanie|
|---|---|---|
|Technologie obejmują wszystko w usługach EOP i Microsoft Defender dla Office 365 P1 oraz:<ul><li>Takie same</li>|<li>**Eksplorator zagrożeń**</li><li>Śledzenie zagrożeń</li><li>Widoki kampanii</li>|<li>Zautomatyzowane badania i odpowiedzi (AIR)</li><li>AIR z Eksploratora zagrożeń</li><li>AIR w przypadku naruszonych użytkowników</li><li>Interfejs API integracji usług SIEM dla zautomatyzowanych badań</li>

Dlatego usługa Microsoft Defender dla Office 365 P2 rozszerza się na stronę badania i  reakcji domu i dodaje nową siłę łętwną. Automatyzacja.

W programie Microsoft Defender Office 365 P2 główne narzędzie do wyszukiwania jest nazywane Eksploratorem **zagrożeń, a** nie wykrywaniem w czasie rzeczywistym. Jeśli zobaczysz Eksploratora zagrożeń podczas przechodzenia do portalu Microsoft 365 Defender, używasz programu Microsoft Defender dla systemu Office 365 P2.

Aby przejść do szczegółów usługi Microsoft Defender dla komputerów Office 365 P1 i P2, **[przejdź do tego artykułu](defender-for-office-365.md)**.

> [!TIP]
> Usługi EOP i Microsoft Defender Office 365 również różnią się w przypadku użytkowników końcowych. W usługach EOP i Defender dla Office 365 P1 celem jest *informacja,* Outlook więc te dwie usługi dodają komunikat "Zgłoś" Outlook, aby użytkownicy mieli możliwość zgłaszania podejrzanych wiadomości *e-mail* w celu dalszej analizy. <p> W programie Defender dla systemu Office 365 P2 (który zawiera wszystko w usługach EOP i P1) fokus przesunie się na dalsze szkolenia dla użytkowników końcowych, dzięki czemu Centrum operacji zabezpieczeń będzie mieć dostęp  do zaawansowanego narzędzia Zagrożeń i jego metryk dla użytkowników końcowych.

## <a name="microsoft-defender-for-office-365-plan-1-vs-plan-2-cheat-sheet"></a>Microsoft Defender dla Office 365 Plan 1 a Plan 2 - ściągawka

Ten podręczny przewodnik pomoże Ci zrozumieć, jakie możliwości posiada każda usługa Microsoft Defender dla Office 365 subskrypcji. W połączeniu z Twoją wiedzą na temat funkcji usługi EOP może ona pomóc twórcom biznesowym w określeniu, która usługa Microsoft Defender for Office 365 najlepiej jaka jest dla nich najlepsza.

|Defender dla Office 365 Plan 1|Defender for Office 365 Plan 2|
|---|---|
|Funkcje konfiguracji, ochrony i wykrywania: <ul><li>[Sejf załączników](safe-attachments.md)</li><li>[Bezpieczne linki](safe-links.md)</li><li>[Sejf załączników do SharePoint, OneDrive i Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[Ochrona przed wyłudzaniem informacji w programie Defender dla Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[Wykrywanie w czasie rzeczywistym](threat-explorer.md)</li></ul>|Funkcje usługi Defender Office 365 Plan 1 <p> --- plus --- <p> Funkcje automatyzacji, badań, rozwiązywania problemów i edukacji: <ul><li>[Śledzenie zagrożeń](threat-trackers.md)</li><li>[Eksplorator zagrożeń](threat-explorer.md)</li><li>[Zautomatyzowane badanie i odpowiedź](office-365-air.md)</li><li>[Szkolenie z symeny ataków](attack-simulation-training.md)</li><li>[Aktywne wyszukiwanie zagrożeń za pomocą zaawansowanego wyszukiwania w Microsoft 365 Defender](../defender/advanced-hunting-overview.md)</li><li>[Badanie zdarzeń w Microsoft 365 Defender](../defender/investigate-incidents.md)</li><li>[Badanie alertów w programie Microsoft 365 Defender](../defender/investigate-alerts.md)</li></ul>|

- Usługa Microsoft Defender dla Office 365 Plan 2 jest zawarta Office 365 E5, Office 365 A5 i Microsoft 365 E5.

- Program Microsoft Defender dla Office 365 Plan 1 jest dołączony do Microsoft 365 Business Premium.

- Program Microsoft Defender dla Office 365 Plan 1 i Defender dla systemu Office 365 Plan 2 są dostępne jako dodatek dla niektórych subskrypcji. Aby dowiedzieć się więcej, oto kolejny link Dostępność funkcji w programie [Microsoft Defender dla Office 365 planów](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

- Funkcja [Sejf dokumenty](safe-docs.md) jest dostępna tylko dla użytkowników z licencjami usługi Microsoft 365 E5 lub Zabezpieczenia platformy Microsoft 365 E5 (nieujętą do programu Microsoft Defender dla Office 365 planów).

- Jeśli Twoja bieżąca subskrypcja nie zawiera programu Microsoft Defender dla usługi Office 365 i [chcesz, skontaktuj](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html) się ze sprzedażą, aby rozpocząć okres próbny i dowiedz się, jak usługa Microsoft Defender dla usługi Office 365 może działać w Twojej organizacji.

- Program Microsoft Defender dla Office 365 P2 ma dostęp do integracji usługi **Microsoft 365 Defender**, co umożliwia efektywne wykrywanie, przeglądanie i reagowanie na zdarzenia i alerty oraz reagowanie na nie.

> [!TIP]
> ***Porada niejawnego programu** testów. Za pomocą spisu docs.microsoft.com można dowiedzieć się więcej o usługach EOP i Microsoft Defender for Office 365. Wróć do tej strony, [Office 365 omówienie](index.yml) zabezpieczeń, a na pasku bocznym zauważysz, że organizacja spisu treści jest organizacją. Proces ten rozpoczyna się od wdrożenia (w tym migracji), a następnie jest w dalszym ciągu zapobieganie, wykrywanie, badanie i reagowanie. <p> Ta struktura jest podzielona, tak aby po tematach _ *Security Administration** były **poruszane tematy dotyczące operacji zabezpieczeń** . Jeśli jesteś nowym członkiem zespołu na stanowisku, skorzystaj z linku zawartego w tej poradce i swojej wiedzy na temat spisu treści, aby dowiedzieć się więcej na ten temat. Pamiętaj, aby na *czas korzystać z linków opinii* i *oceniać* artykuły. Opinie pomagają nam ulepszać to, co oferujemy.

## <a name="where-to-go-next"></a>Gdzie przejść dalej

Jeśli jesteś administratorem zabezpieczeń, może być konieczne skonfigurowanie DKIM lub DMARC dla poczty. Możesz chcieć, aby dla użytkowników priorytetowych było publikowane "Ścisłe" ustawienia wstępne zabezpieczeń, lub poszukać nowych nowości w tym produkcie. Jeśli natomiast korzystasz z usługi Security Ops, możesz chcieć korzystać z wykrywania w czasie rzeczywistym lub Eksploratora zagrożeń w celu zbadania i reakcji albo przeprowadzić wykrywanie użytkowników końcowych za pomocą ataku i odpowiedzi. Tak czy inaczej, poniżej poszło kilka dodatkowych zaleceń, które należy sprawdzić w następnych krokach.

[Uwierzytelnianie poczty e-mail, w tym SPF, DKIM i DMARC (z linkami do konfiguracji wszystkich trzech)](email-validation-and-authentication.md)

[Zapoznaj się z zalecanymi "złotymi" konfiguracjami](recommended-settings-for-eop-and-office365.md) i użyj ich zalecanych ustawień wstępnych, [aby szybko skonfigurować zasady zabezpieczeń](preset-security-policies.md)

Nadrabiaj zaległości w tym, co nowego w [programie Microsoft Defender dla Office 365 (w tym nad rozwojem usługi EOP)](whats-new-in-defender-for-office-365.md)

[Korzystanie z wykrywania w Eksploratorze zagrożeń lub w czasie rzeczywistym](threat-explorer.md)

Korzystanie ze [szkolenia symulacyjnego w zakresie ataków](attack-simulation-training.md)
