---
title: zabezpieczenia Office 365, w tym Ochrona usługi Office 365 w usłudze Microsoft Defender i Exchange Online Protection
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 07/21/2021
audience: Admin
ms.topic: conceptual
ms.localizationpriority: high
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Zabezpieczenia w Office 365, od EOP do planów Ochrona usługi Office 365 w usłudze Defender 1 i 2, standardowa i ścisła konfiguracja zabezpieczeń i nie tylko. Dowiedz się, co masz i jak zabezpieczyć swoje właściwości.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a9f480575c712488a17dc7e9e91320edc11d0e50
ms.sourcegitcommit: 5eff41a350a01e18d9cdd572c9d8ff99d6c9563a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2022
ms.locfileid: "64835914"
---
# <a name="microsoft-defender-for-office-365-security-overview"></a>Omówienie zabezpieczeń Ochrona usługi Office 365 w usłudze Microsoft Defender

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)

W tym artykule przedstawiono nowe właściwości zabezpieczeń Ochrona usługi Office 365 w usłudze Microsoft Defender w chmurze. Niezależnie od tego, czy jesteś częścią centrum operacji zabezpieczeń, jesteś nowym administratorem zabezpieczeń w tej przestrzeni, czy chcesz odświeżać, zacznijmy.

> [!CAUTION]
> Jeśli używasz **witryny Outlook.com**, **Microsoft 365 Family** lub **Microsoft 365 Personal** i potrzebujesz informacji *o* *linkach Sejf lub załącznikach Sejf*, ***kliknij ten link***: [Zaawansowane zabezpieczenia Outlook.com dla Microsoft 365 subskrybentów](https://support.microsoft.com/office/advanced-outlook-com-security-for-office-365-subscribers-882d2243-eab9-4545-a58a-b36fee4a46e2).

## <a name="what-is-defender-for-office-365-security"></a>Co to są zabezpieczenia Ochrona usługi Office 365 w usłudze Defender

Każda subskrypcja Office 365 ma funkcje zabezpieczeń. Cele i akcje, które można podjąć, zależą od ukierunkowania tych różnych subskrypcji. W Office 365 zabezpieczeń istnieją trzy główne usługi zabezpieczeń (lub produkty) powiązane z typem subskrypcji:

1. Exchange Online Protection (EOP)
1. Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 (Defender for Office P1)
1. Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2 (Defender for Office P2)

> [!NOTE]
> Jeśli subskrypcja została zakupiona i musisz *teraz* wdrożyć funkcje zabezpieczeń, przejdź do kroków [opisanych w artykule Ochrona przed zagrożeniami](protect-against-threats.md) . Jeśli dopiero zaczynasz swoją subskrypcję i chcesz poznać swoją licencję przed rozpoczęciem, przejdź do obszaru Rozliczenia > Produkty w [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com/AdminPortal/#/homepage).

Office 365 zabezpieczenia bazują na podstawowych zabezpieczeniach oferowanych przez EOP. EOP jest obecny w dowolnej subskrypcji, w której można znaleźć Exchange Online skrzynki pocztowe (pamiętaj, że wszystkie produkty zabezpieczeń omówione tutaj są oparte na chmurze).

Możesz być przyzwyczajony do tego, że te trzy składniki zostały omówione w ten sposób:

|EOP|Ochrona usługi Office 365 w usłudze Microsoft Defender P1|Ochrona usługi Office 365 w usłudze Microsoft Defender P2|
|---|---|---|
|Zapobiega szerokim, opartym na woluminie, znanym atakom.|Chroni pocztę e-mail i współpracę przed złośliwym oprogramowaniem, złośliwym oprogramowaniem i złośliwym oprogramowaniem oraz naruszeniem zabezpieczeń poczty e-mail w firmie.|Dodaje badania po naruszeniu zabezpieczeń, wyszukiwanie zagrożeń i reagowanie, a także automatyzację i symulację (na potrzeby trenowania).|

Ale jeśli chodzi o architekturę, zacznijmy od myślenia o każdym kawałku jako skumulowanych warstwach zabezpieczeń, z których każda ma nacisk na bezpieczeństwo. Bardziej podobny do następującego:

:::image type="content" source="../../media/tp_GraphicEOPATPP1P2_2.png" alt-text="EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender i ich relacje ze sobą z naciskiem na usługę, w tym notatkę dotyczącą uwierzytelniania za pośrednictwem poczty e-mail" lightbox="../../media/tp_GraphicEOPATPP1P2_2.png":::

Mimo że każda z tych usług podkreśla cel spośród funkcji Ochrona, Wykrywanie, Badanie i Reagowanie, ***all** _ usługi mogą realizować _ *_dowolne_** cele ochrony, wykrywania, badania i reagowania.

Podstawą zabezpieczeń Office 365 jest ochrona EOP. Ochrona usługi Office 365 w usłudze Microsoft Defender P1 zawiera w nim EOP. Ochrona usługi Office 365 w usłudze Defender P2 zawiera P1 i EOP. Struktura jest skumulowana. Dlatego podczas konfigurowania tego produktu należy zacząć od EOP i pracować nad Ochrona usługi Office 365 w usłudze Defender.

Mimo że konfiguracja uwierzytelniania poczty e-mail odbywa się w publicznym systemie DNS, ważne jest, aby skonfigurować tę funkcję w celu ochrony przed fałszowaniem. *Jeśli masz funkcję EOP,* ***należy [skonfigurować uwierzytelnianie poczty e-mail](email-validation-and-authentication.md)***.

Jeśli masz Office 365 E3 lub poniżej, masz EOP, ale z opcją zakupu autonomicznego Ochrona usługi Office 365 w usłudze Defender P1 poprzez uaktualnienie. Jeśli masz Office 365 E5, masz już Ochrona usługi Office 365 w usłudze Defender P2.

> [!TIP]
> Jeśli Twoja subskrypcja nie jest Office 365 E3 lub E5, nadal możesz sprawdzić, czy masz możliwość uaktualnienia do Ochrona usługi Office 365 w usłudze Microsoft Defender P1. Jeśli cię to interesuje, [ta strona internetowa](https://www.microsoft.com/microsoft-365/exchange/advance-threat-protection#coreui-contentrichblock-x07wids) zawiera listę subskrypcji kwalifikujących się do uaktualnienia Ochrona usługi Office 365 w usłudze Microsoft Defender P1 (sprawdź koniec strony, aby uzyskać szczegółowe informacje).

## <a name="the-office-365-security-ladder-from-eop-to-microsoft-defender-for-office-365"></a>Drabina zabezpieczeń Office 365 od EOP do Ochrona usługi Office 365 w usłudze Microsoft Defender

> [!IMPORTANT]
> Poznaj szczegóły na tych stronach: [Exchange Online Protection](exchange-online-protection-overview.md) i [Ochrona usługi Office 365 w usłudze Defender](defender-for-office-365.md).

Co sprawia, że dodawanie planów Ochrona usługi Office 365 w usłudze Microsoft Defender jest zaletą czystego zarządzania zagrożeniami EOP, na pierwszy rzut oka może być trudne. Aby ustalić, czy ścieżka uaktualnienia jest odpowiednia dla Twojej organizacji, przyjrzyjmy się możliwościom każdego produktu, jeśli chodzi o:

- zapobieganie zagrożeniom i ich wykrywanie
- Badania
- Odpowiadać

począwszy od **Exchange Online Protection**:
<p>

|Zapobieganie/wykrywanie|Zbadaj|Odpowiadanie|
|---|---|---|
|Technologie obejmują:<ul><li>Spam</li><li>Phish</li><li>Złośliwego oprogramowania</li><li>poczta zbiorcza</li><li>fałszowanie inteligencji</li><li>wykrywanie personifikacji</li><li>Kwarantanna administratora</li><li>Przesyłanie przez administratora i użytkownika wyników fałszywie dodatnich i fałszywie ujemnych</li><li>Zezwalaj/blokuj dla adresów URL i plików</li><li>Raporty</li></ul>|<li>Przeszukiwanie dzienników inspekcji</li><li>Ślad komunikatu</li>|<li>Automatyczne przeczyszczanie o zerowej godzinie (ZAP)</li><li>Uściślanie i testowanie list dozwolonych i blokowych</li>|

Jeśli chcesz przejść do EOP, **[przejdź do tego artykułu](exchange-online-protection-overview.md)**.

Ponieważ te produkty są skumulowane, jeśli ocenisz Ochrona usługi Office 365 w usłudze Microsoft Defender P1 i zdecydujesz się go zasubskrybować, dodasz te możliwości.

Zyski z **Ochrona usługi Office 365 w usłudze Defender, plan 1** (do tej pory):
<p>

|Zapobieganie/wykrywanie|Zbadaj|Odpowiadanie|
|---|---|---|
|Technologie obejmują wszystko w ramach EOP plus:<ul><li>załączniki Sejf</li><li>linki Sejf<li>Ochrona usługi Office 365 w usłudze Microsoft Defender ochronę obciążeń (np. SharePoint Online, Teams, OneDrive dla Firm)</li><li>Ochrona przed kliknięciem w wiadomościach e-mail, klientach Office i Teams</li><li>ochrona przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender</li><li>Ochrona przed personifikacją użytkowników i domen</li><li>Alerty i interfejs API integracji SIEM dla alertów</li>|<li>Interfejs API integracji rozwiązania SIEM na potrzeby wykrywania</li><li>**Narzędzie do wykrywania w czasie rzeczywistym**</li><li>Śledzenie adresu URL</li>|<li>Tym samym</li></ul>

Dlatego Ochrona usługi Office 365 w usłudze Microsoft Defender P1 rozszerza się po stronie ***zapobiegania** _ domu i dodaje dodatkowe formy _*_wykrywania_**.

Ochrona usługi Office 365 w usłudze Microsoft Defender P1 dodaje również **wykrywanie w czasie rzeczywistym** na potrzeby badań. Nazwa tego narzędzia do wyszukiwania zagrożeń jest pogrubiona, ponieważ jest jasne, *że wiesz,* że masz Ochrona usługi Office 365 w usłudze Defender P1. Nie pojawia się w Ochrona usługi Office 365 w usłudze Defender P2.

Zyski z **Ochrona usługi Office 365 w usłudze Defender, plan 2** (do tej pory):
<p>

|Zapobieganie/wykrywanie|Zbadaj|Odpowiadanie|
|---|---|---|
|Technologie obejmują wszystko w ramach EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender P1 plus:<ul><li>Tym samym</li>|<li>**Eksplorator zagrożeń**</li><li>Moduły śledzące zagrożenia</li><li>Widoki kampanii</li>|<li>Zautomatyzowane badanie i reagowanie (AIR)</li><li>AIR z Eksploratora zagrożeń</li><li>AIR dla użytkowników z naruszonymi zabezpieczeniami</li><li>Interfejs API integracji SIEM na potrzeby zautomatyzowanych badań</li>

Tak więc Ochrona usługi Office 365 w usłudze Microsoft Defender P2 rozszerza ***stronę badania i odpowiedzi*** domu i dodaje nową siłę polowania. Automatyzacji.

W Ochrona usługi Office 365 w usłudze Microsoft Defender P2 podstawowym narzędziem do wyszukiwania zagrożeń jest **Eksplorator zagrożeń**, a nie wykrywanie w czasie rzeczywistym. Jeśli podczas przechodzenia do portalu Microsoft 365 Defender widzisz Eksploratora zagrożeń, znajdujesz się w Ochrona usługi Office 365 w usłudze Microsoft Defender P2.

Aby zapoznać się ze szczegółami Ochrona usługi Office 365 w usłudze Microsoft Defender P1 i P2, **[przejdź do tego artykułu](defender-for-office-365.md)**.

> [!TIP]
> Metodyka EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender są również różne, jeśli chodzi o użytkowników końcowych. W modelu EOP i Ochrona usługi Office 365 w usłudze Defender P1 skupiamy się na *świadomości*, dlatego te dwie usługi zawierają *komunikat raportu Outlook dodatku*, aby użytkownicy mogli zgłaszać wiadomości e-mail, które uważają za podejrzane, w celu dalszej analizy. <p> W Ochrona usługi Office 365 w usłudze Defender P2 (który zawiera wszystkie elementy EOP i P1) fokus przenosi się na *dalsze szkolenia* dla użytkowników końcowych, dlatego centrum operacji zabezpieczeń ma dostęp do zaawansowanego narzędzia *symulatora zagrożeń* i udostępnianych metryk użytkowników końcowych.

## <a name="microsoft-defender-for-office-365-plan-1-vs-plan-2-cheat-sheet"></a>Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 a ściągawka Plan 2

Ta szybka dokumentacja pomoże Ci zrozumieć, jakie możliwości mają poszczególne Ochrona usługi Office 365 w usłudze Microsoft Defender subskrypcji. W połączeniu z twoją wiedzą na temat funkcji EOP może pomóc decydentom biznesowym określić, jakie Ochrona usługi Office 365 w usłudze Microsoft Defender są najlepsze dla ich potrzeb.

|Ochrona usługi Office 365 w usłudze Defender plan 1|Ochrona usługi Office 365 w usłudze Defender plan 2|
|---|---|
|Możliwości konfiguracji, ochrony i wykrywania: <ul><li>[załączniki Sejf](safe-attachments.md)</li><li>[Bezpieczne linki](safe-links.md)</li><li>[Bezpieczne załączniki dla programu SharePoint, usługi OneDrive i aplikacji Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[Ochrona przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[Wykrywanie w czasie rzeczywistym](threat-explorer.md)</li></ul>|Ochrona usługi Office 365 w usłudze Defender plan 1 — możliwości <p> --- plus --- <p> Możliwości automatyzacji, badania, korygowania i edukacji: <ul><li>[Moduły śledzące zagrożenia](threat-trackers.md)</li><li>[Eksplorator zagrożeń](threat-explorer.md)</li><li>[Zautomatyzowane badanie i reagowanie](office-365-air.md)</li><li>[Trenowanie symulacji ataków](attack-simulation-training.md)</li><li>[Proaktywne wyszukiwanie zagrożeń dzięki zaawansowanym polowaniom w Microsoft 365 Defender](../defender/advanced-hunting-overview.md)</li><li>[Badanie zdarzeń w Microsoft 365 Defender](../defender/investigate-incidents.md)</li><li>[Badanie alertów w Microsoft 365 Defender](../defender/investigate-alerts.md)</li></ul>|

- Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2 jest uwzględniony w Office 365 E5, Office 365 A5 i Microsoft 365 E5.

- Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 jest uwzględniony w Microsoft 365 Business Premium.

- Ochrona usługi Office 365 w usłudze Microsoft Defender Plan 1 i Ochrona usługi Office 365 w usłudze Defender Plan 2 są dostępne jako dodatek dla niektórych subskrypcji. Aby dowiedzieć się więcej, oto kolejny link [Dostępność funkcji w planach Ochrona usługi Office 365 w usłudze Microsoft Defender](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

- Funkcja [dokumenty Sejf](safe-docs.md) jest dostępna tylko dla użytkowników z licencjami Microsoft 365 E5 lub Zabezpieczenia platformy Microsoft 365 E5 (nieobjętymi Ochrona usługi Office 365 w usłudze Microsoft Defender planów).

- Jeśli bieżąca subskrypcja nie zawiera Ochrona usługi Office 365 w usłudze Microsoft Defender i chcesz, [skontaktuj się ze sprzedażą, aby rozpocząć wersję próbną](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html), i dowiedz się, jak Ochrona usługi Office 365 w usłudze Microsoft Defender mogą działać w organizacji.

- Ochrona usługi Office 365 w usłudze Microsoft Defender klienci P2 mają dostęp do **integracji Microsoft 365 Defender** w celu wydajnego wykrywania, przeglądania i reagowania na zdarzenia i alerty.

> [!TIP]
> ***Wskazówka dla niejawnych testerów** _. Aby dowiedzieć się więcej na temat EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender, możesz użyć spisu treści docs.microsoft.com. Wróć do tej strony, [Office 365 Omówienie zabezpieczeń](index.yml). Zauważysz, że organizacja spisu treści znajduje się na pasku bocznym. Rozpoczyna się od wdrożenia (w tym migracji), a następnie kontynuuje zapobieganie, wykrywanie, badanie i reagowanie. <p> Ta struktura jest podzielona tak, aby tematy _ *Administracja zabezpieczeniami** były obserwowane w tematach **Operacje zabezpieczeń** . Jeśli jesteś nowym członkiem którejś z ról zadań, skorzystaj z linku w tej poradzie i swojej wiedzy na temat spisu treści, aby dowiedzieć się więcej o przestrzeni. Pamiętaj, aby używać *linków do opinii* i *oceniać artykuły* zgodnie z rzeczywistym użyciem. Opinie pomagają nam ulepszyć oferowane przez nas oferty.

## <a name="where-to-go-next"></a>Gdzie iść dalej

Jeśli jesteś administratorem zabezpieczeń, może być konieczne skonfigurowanie DKIM lub DMARC dla poczty. Możesz wprowadzić "ścisłe" ustawienia wstępne zabezpieczeń dla użytkowników o priorytecie lub poszukać nowości w produkcie. Jeśli korzystasz z usługi Security Ops, możesz użyć funkcji wykrywania w czasie rzeczywistym lub Eksploratora zagrożeń, aby zbadać i zareagować, lub wytrenować wykrywanie użytkowników końcowych za pomocą symulatora ataków. Tak czy inaczej, oto kilka dodatkowych zaleceń dotyczących tego, co należy przyjrzeć się dalej.

[Uwierzytelnianie poczty e-mail, w tym SPF, DKIM i DMARC (z linkami do konfiguracji wszystkich trzech)](email-validation-and-authentication.md)

[Zapoznaj się z konkretnymi zalecanymi konfiguracjami "golden"](recommended-settings-for-eop-and-office365.md) i [użyj zalecanych ustawień wstępnych, aby szybko skonfigurować zasady zabezpieczeń](preset-security-policies.md)

Nadrabiaj zaległości w [zakresie nowości w Ochrona usługi Office 365 w usłudze Microsoft Defender (w tym rozwoju EOP)](whats-new-in-defender-for-office-365.md)

[Używanie Eksploratora zagrożeń lub wykrywania w czasie rzeczywistym](threat-explorer.md)

[Korzystanie z trenowania symulacji ataków](attack-simulation-training.md)
