---
title: Zabezpieczenia usługi Office 365, w tym usługa Microsoft Defender dla usługi Office 365 i usługa Exchange Online Protection
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
description: Zabezpieczenia w usłudze Office 365, od EOP do usługi Defender dla planów 1 i 2 usługi Office 365, standardowa i ścisła konfiguracja zabezpieczeń i nie tylko. Dowiedz się, co masz i jak zabezpieczyć swoje właściwości.
ms.technology: mdo
ms.prod: m365-security
adobe-target: true
ms.openlocfilehash: a5a7a4e78ae3b160b565e253d315d94fc5b6b53a
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2022
ms.locfileid: "65940915"
---
# <a name="microsoft-defender-for-office-365-security-overview"></a>Omówienie zabezpieczeń usługi Microsoft Defender dla usługi Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)

W tym artykule przedstawiono nowe właściwości zabezpieczeń usługi Microsoft Defender dla usługi Office 365 w chmurze. Niezależnie od tego, czy jesteś częścią centrum operacji zabezpieczeń, jesteś nowym administratorem zabezpieczeń w tej przestrzeni, czy chcesz odświeżać, zacznijmy.

> [!CAUTION]
> Jeśli używasz **Outlook.com**, **rodziny microsoft 365** lub **usługi Microsoft 365 Personal** i potrzebujesz informacji o *bezpiecznych linkach* lub *bezpiecznych załącznikach* , ***kliknij ten link***: [Zaawansowane zabezpieczenia Outlook.com dla subskrybentów platformy Microsoft 365](https://support.microsoft.com/office/advanced-outlook-com-security-for-office-365-subscribers-882d2243-eab9-4545-a58a-b36fee4a46e2).

## <a name="what-is-defender-for-office-365-security"></a>Co to jest zabezpieczenia usługi Defender dla usługi Office 365

Każda subskrypcja usługi Office 365 ma funkcje zabezpieczeń. Cele i akcje, które można podjąć, zależą od ukierunkowania tych różnych subskrypcji. W zabezpieczeniach usługi Office 365 istnieją trzy główne usługi zabezpieczeń (lub produkty) powiązane z typem subskrypcji:

1. Exchange Online Protection (EOP)
1. Microsoft Defender for Office 365 Plan 1 (Defender for Office P1)
1. Microsoft Defender for Office 365 Plan 2 (Defender for Office P2)

> [!NOTE]
> Jeśli subskrypcja została zakupiona i musisz *teraz* wdrożyć funkcje zabezpieczeń, przejdź do kroków [opisanych w artykule Ochrona przed zagrożeniami](protect-against-threats.md) . Jeśli dopiero zaczynasz swoją subskrypcję i chcesz poznać swoją licencję przed rozpoczęciem, przejdź do obszaru Rozliczenia > Produkty w [centrum administracyjnym platformy Microsoft 365](https://admin.microsoft.com/AdminPortal/#/homepage).

Zabezpieczenia usługi Office 365 bazują na podstawowych zabezpieczeniach oferowanych przez funkcję EOP. Funkcja EOP jest obecna w dowolnej subskrypcji, w której można znaleźć skrzynki pocztowe usługi Exchange Online (pamiętaj, że wszystkie produkty zabezpieczeń omówione tutaj są oparte na chmurze).

Możesz być przyzwyczajony do tego, że te trzy składniki zostały omówione w ten sposób:

|EOP|Microsoft Defender dla usługi Office 365 P1|Microsoft Defender dla usługi Office 365 P2|
|---|---|---|
|Zapobiega szerokim, opartym na woluminie, znanym atakom.|Chroni pocztę e-mail i współpracę przed złośliwym oprogramowaniem, złośliwym oprogramowaniem i złośliwym oprogramowaniem oraz naruszeniem zabezpieczeń poczty e-mail w firmie.|Dodaje badania po naruszeniu zabezpieczeń, wyszukiwanie zagrożeń i reagowanie, a także automatyzację i symulację (na potrzeby trenowania).|

Ale jeśli chodzi o architekturę, zacznijmy od myślenia o każdym kawałku jako skumulowanych warstwach zabezpieczeń, z których każda ma nacisk na bezpieczeństwo. Bardziej podobny do następującego:

:::image type="content" source="../../media/tp_GraphicEOPATPP1P2_2.png" alt-text="EOP i Microsoft Defender dla usługi Office 365 oraz ich relacje ze sobą z wyróżnieniem usługi, w tym notatka dotycząca uwierzytelniania za pośrednictwem poczty e-mail" lightbox="../../media/tp_GraphicEOPATPP1P2_2.png":::

Mimo że każda z tych usług podkreśla cel spośród funkcji Ochrona, Wykrywanie, Badanie i Reagowanie, ***all** _ usługi mogą realizować _ *_dowolne_** cele ochrony, wykrywania, badania i reagowania.

Rdzeniem zabezpieczeń usługi Office 365 jest ochrona na potrzeby EOP. Usługa Microsoft Defender dla usługi Office 365 P1 zawiera w niej operację EOP. Usługa Defender dla usługi Office 365 P2 zawiera metody P1 i EOP. Struktura jest skumulowana. Dlatego podczas konfigurowania tego produktu należy zacząć od EOP i pracować z usługą Defender dla usługi Office 365.

Mimo że konfiguracja uwierzytelniania poczty e-mail odbywa się w publicznym systemie DNS, ważne jest, aby skonfigurować tę funkcję w celu ochrony przed fałszowaniem. *Jeśli masz funkcję EOP,* ***należy [skonfigurować uwierzytelnianie poczty e-mail](email-validation-and-authentication.md)***.

Jeśli masz usługę Office 365 E3 lub nowszą, masz funkcję EOP, ale z opcją zakupu autonomicznej usługi Defender dla usługi Office 365 P1 poprzez uaktualnienie. Jeśli masz usługę Office 365 E5, masz już usługę Defender dla usługi Office 365 P2.

> [!TIP]
> Jeśli Twoja subskrypcja nie jest usługą Office 365 E3 lub E5, nadal możesz sprawdzić, czy masz możliwość uaktualnienia do usługi Microsoft Defender dla usługi Office 365 P1. Jeśli cię to interesuje, [ta strona internetowa](https://www.microsoft.com/microsoft-365/exchange/advance-threat-protection#coreui-contentrichblock-x07wids) zawiera listę subskrypcji kwalifikujących się do uaktualnienia usługi Microsoft Defender dla usługi Office 365 P1 (sprawdź koniec strony, aby uzyskać szczegółowe informacje).

## <a name="the-office-365-security-ladder-from-eop-to-microsoft-defender-for-office-365"></a>Drabina zabezpieczeń usługi Office 365 z EOP do usługi Microsoft Defender dla usługi Office 365

> [!IMPORTANT]
> Poznaj szczegóły na tych stronach: [Exchange Online Protection](exchange-online-protection-overview.md) i [Defender for Office 365](defender-for-office-365.md).

To, co sprawia, że dodawanie planów usługi Microsoft Defender dla usługi Office 365 jest zaletą czystego zarządzania zagrożeniami EOP, może być trudne do odpowiedzenia na pierwszy rzut oka. Aby ustalić, czy ścieżka uaktualnienia jest odpowiednia dla Twojej organizacji, przyjrzyjmy się możliwościom każdego produktu, jeśli chodzi o:

- zapobieganie zagrożeniom i ich wykrywanie
- Badania
- Odpowiadać

począwszy od **programu Exchange Online Protection**:
<p>

|Zapobieganie/wykrywanie|Zbadaj|Odpowiadanie|
|---|---|---|
|Technologie obejmują:<ul><li>Spam</li><li>Phish</li><li>Złośliwego oprogramowania</li><li>poczta zbiorcza</li><li>fałszowanie inteligencji</li><li>wykrywanie personifikacji</li><li>Kwarantanna administratora</li><li>Przesyłanie przez administratora i użytkownika wyników fałszywie dodatnich i fałszywie ujemnych</li><li>Zezwalaj/blokuj dla adresów URL i plików</li><li>Raporty</li></ul>|<li>Przeszukiwanie dzienników inspekcji</li><li>Ślad komunikatu</li>|<li>Automatyczne przeczyszczanie (ZAP)</li><li>Uściślanie i testowanie list dozwolonych i blokowych</li>|

Jeśli chcesz przejść do EOP, **[przejdź do tego artykułu](exchange-online-protection-overview.md)**.

Ponieważ te produkty są skumulowane, jeśli ocenisz usługę Microsoft Defender dla usługi Office 365 P1 i zdecydujesz się ją subskrybować, dodasz te możliwości.

Zyski z **usługi Defender dla usługi Office 365, plan 1** (do tej pory):
<p>

|Zapobieganie/wykrywanie|Zbadaj|Odpowiadanie|
|---|---|---|
|Technologie obejmują wszystko w ramach EOP plus:<ul><li>Bezpieczne załączniki</li><li>Bezpieczne linki<li>Ochrona usługi Microsoft Defender dla usługi Office 365 dla obciążeń (np. SharePoint Online, Teams, OneDrive dla Firm)</li><li>Ochrona przed kliknięciem w wiadomościach e-mail, klientach pakietu Office i aplikacji Teams</li><li>ochrona przed wyłudzaniem informacji w usłudze Defender dla usługi Office 365</li><li>Ochrona przed personifikacją użytkowników i domen</li><li>Alerty i interfejs API integracji SIEM dla alertów</li>|<li>Interfejs API integracji rozwiązania SIEM na potrzeby wykrywania</li><li>**Narzędzie do wykrywania w czasie rzeczywistym**</li><li>Śledzenie adresu URL</li>|<li>Tym samym</li></ul>

Dlatego usługa Microsoft Defender dla usługi Office 365 P1 rozwija się po stronie ***zapobiegania** _ domu i dodaje dodatkowe formy _wykrywania_ _***.

Usługa Microsoft Defender dla usługi Office 365 P1 dodaje również **wykrywanie w czasie rzeczywistym** na potrzeby badań. Nazwa tego narzędzia do wyszukiwania zagrożeń jest pogrubiona, ponieważ jest jasne, *że masz* usługę Defender dla usługi Office 365 P1. Nie jest on wyświetlany w usłudze Defender dla usługi Office 365 P2.

Zyski z **usługi Defender dla usługi Office 365, plan 2** (do tej pory):
<p>

|Zapobieganie/wykrywanie|Zbadaj|Odpowiadanie|
|---|---|---|
|Technologie obejmują wszystkie elementy EOP i Microsoft Defender dla usługi Office 365 P1 plus:<ul><li>Tym samym</li>|<li>**Eksplorator zagrożeń**</li><li>Moduły śledzące zagrożenia</li><li>Widoki kampanii</li>|<li>Zautomatyzowane badanie i reagowanie (AIR)</li><li>AIR z Eksploratora zagrożeń</li><li>AIR dla użytkowników z naruszonymi zabezpieczeniami</li><li>Interfejs API integracji SIEM na potrzeby zautomatyzowanych badań</li>

Dlatego usługa Microsoft Defender dla usługi Office 365 P2 rozszerza stronę ***badania i odpowiedzi*** w domu i dodaje nową siłę wyszukiwania zagrożeń. Automatyzacji.

W usłudze Microsoft Defender dla usługi Office 365 P2 podstawowe narzędzie do wyszukiwania zagrożeń jest nazywane **Eksploratorem zagrożeń** , a nie wykrywaniem w czasie rzeczywistym. Jeśli podczas przechodzenia do portalu usługi Microsoft 365 Defender zostanie wyświetlony Eksplorator zagrożeń, korzystasz z usługi Microsoft Defender dla usługi Office 365 P2.

Aby zapoznać się ze szczegółami usługi Microsoft Defender dla usług Office 365 P1 i P2, **[przejdź do tego artykułu](defender-for-office-365.md)**.

> [!TIP]
> Metodyka EOP i usługa Microsoft Defender dla usługi Office 365 również różnią się w przypadku użytkowników końcowych. W usługach EOP i Defender for Office 365 P1 skupiono się na *świadomości*, dlatego te dwie usługi obejmują *dodatek Outlook dotyczący wiadomości raportu* , dzięki czemu użytkownicy mogą zgłaszać wiadomości e-mail, które uważają za podejrzane, w celu dalszej analizy. <p> W usłudze Defender dla usługi Office 365 P2 (która zawiera wszystko w ramach operacji EOP i P1) fokus przenosi się na *dalsze szkolenia* dla użytkowników końcowych, dlatego centrum operacji zabezpieczeń ma dostęp do zaawansowanego narzędzia *symulatora zagrożeń* i udostępnianych metryk użytkowników końcowych.

## <a name="microsoft-defender-for-office-365-plan-1-vs-plan-2-cheat-sheet"></a>Ściągawka Microsoft Defender for Office 365 Plan 1 a Plan 2

Ta szybka dokumentacja pomoże Ci zrozumieć, jakie możliwości mają poszczególne subskrypcje usługi Microsoft Defender dla usługi Office 365. W połączeniu z twoją wiedzą na temat funkcji EOP może pomóc decydentom biznesowym określić, co usługa Microsoft Defender dla usługi Office 365 jest najlepsza dla ich potrzeb.

|Defender for Office 365 Plan 1|Defender for Office 365 Plan 2|
|---|---|
|Możliwości konfiguracji, ochrony i wykrywania: <ul><li>[Bezpieczne załączniki](safe-attachments.md)</li><li>[Bezpieczne linki](safe-links.md)</li><li>[Bezpieczne załączniki dla programu SharePoint, usługi OneDrive i aplikacji Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[Ochrona przed wyłudzaniem informacji w usłudze Defender dla usługi Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[Wykrywanie w czasie rzeczywistym](threat-explorer.md)</li></ul>|Możliwości usługi Defender dla usługi Office 365 Plan 1 <p> --- plus --- <p> Możliwości automatyzacji, badania, korygowania i edukacji: <ul><li>[Moduły śledzące zagrożenia](threat-trackers.md)</li><li>[Eksplorator zagrożeń](threat-explorer.md)</li><li>[Zautomatyzowane badanie i reagowanie](office-365-air.md)</li><li>[Trenowanie symulacji ataków](attack-simulation-training.md)</li><li>[Proaktywne wyszukiwanie zagrożeń przy użyciu zaawansowanego wyszukiwania zagrożeń w usłudze Microsoft 365 Defender](../defender/advanced-hunting-overview.md)</li><li>[Badanie zdarzeń w usłudze Microsoft 365 Defender](../defender/investigate-incidents.md)</li><li>[Badanie alertów w usłudze Microsoft 365 Defender](../defender/investigate-alerts.md)</li></ul>|

- Usługa Microsoft Defender dla usługi Office 365 Plan 2 jest uwzględniona w usługach Office 365 E5, Office 365 A5 i Microsoft 365 E5.

- Usługa Microsoft Defender dla usługi Office 365 Plan 1 jest uwzględniona w usłudze Microsoft 365 Business Premium.

- Usługi Microsoft Defender dla usługi Office 365 Plan 1 i Defender dla usługi Office 365 Plan 2 są dostępne jako dodatek dla niektórych subskrypcji. Aby dowiedzieć się więcej, oto kolejny link [Dostępność funkcji w planach usługi Microsoft Defender dla usługi Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

- Funkcja [Bezpieczne dokumenty](safe-docs.md) jest dostępna tylko dla użytkowników z licencjami microsoft 365 E5 lub Microsoft 365 E5 Security (nieuwzględnianych w planach usługi Microsoft Defender dla usługi Office 365).

- Jeśli bieżąca subskrypcja nie obejmuje usługi Microsoft Defender dla usługi Office 365 i chcesz jej użyć, [skontaktuj się ze sprzedażą, aby rozpocząć wersję próbną](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html), i dowiedz się, jak usługa Microsoft Defender dla usługi Office 365 może działać w Twojej organizacji.

- Klienci usługi Microsoft Defender dla usługi Office 365 P2 mają dostęp do **integracji usługi Microsoft 365 Defender** w celu wydajnego wykrywania, przeglądania i reagowania na zdarzenia i alerty oraz reagowania na nie.

> [!TIP]
> ***Wskazówka dla niejawnych testerów** _. Aby dowiedzieć się więcej na temat EOP i usługi Microsoft Defender dla usługi Office 365, możesz użyć spisu treści docs.microsoft.com. Wróć do tej strony, [omówienie zabezpieczeń usługi Office 365](index.yml), a zauważysz, że organizacja spisu treści znajduje się na pasku bocznym. Rozpoczyna się od wdrożenia (w tym migracji), a następnie kontynuuje zapobieganie, wykrywanie, badanie i reagowanie. <p> Ta struktura jest podzielona tak, aby tematy _ *Administracja zabezpieczeniami** były obserwowane w tematach **Operacje zabezpieczeń** . Jeśli jesteś nowym członkiem którejś z ról zadań, skorzystaj z linku w tej poradzie i swojej wiedzy na temat spisu treści, aby dowiedzieć się więcej o przestrzeni. Pamiętaj, aby używać *linków do opinii* i *oceniać artykuły* zgodnie z rzeczywistym użyciem. Opinie pomagają nam ulepszyć oferowane przez nas oferty.

## <a name="where-to-go-next"></a>Gdzie iść dalej

Jeśli jesteś administratorem zabezpieczeń, może być konieczne skonfigurowanie DKIM lub DMARC dla poczty. Możesz wprowadzić "ścisłe" ustawienia wstępne zabezpieczeń dla użytkowników o priorytecie lub poszukać nowości w produkcie. Jeśli korzystasz z usługi Security Ops, możesz użyć funkcji wykrywania w czasie rzeczywistym lub Eksploratora zagrożeń, aby zbadać i zareagować, lub wytrenować wykrywanie użytkowników końcowych za pomocą symulatora ataków. Tak czy inaczej, oto kilka dodatkowych zaleceń dotyczących tego, co należy przyjrzeć się dalej.

[Uwierzytelnianie poczty e-mail, w tym SPF, DKIM i DMARC (z linkami do konfiguracji wszystkich trzech)](email-validation-and-authentication.md)

[Zapoznaj się z konkretnymi zalecanymi konfiguracjami "golden"](recommended-settings-for-eop-and-office365.md) i [użyj zalecanych ustawień wstępnych, aby szybko skonfigurować zasady zabezpieczeń](preset-security-policies.md)

Nadrabiaj zaległości w zakresie [nowości w usłudze Microsoft Defender dla usługi Office 365 (w tym rozwoju EOP)](whats-new-in-defender-for-office-365.md)

[Używanie Eksploratora zagrożeń lub wykrywania w czasie rzeczywistym](threat-explorer.md)

[Korzystanie z trenowania symulacji ataków](attack-simulation-training.md)
