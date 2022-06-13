---
title: Microsoft 365 Security for Business Decision Makers (BDMs)
description: Najczęstsze scenariusze zagrożeń i ataków, z którymi obecnie borykają się organizacje w swoich środowiskach Microsoft 365, oraz zalecane działania w celu ograniczenia tych zagrożeń.
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
manager: johmar
audience: Admin
ms.topic: tutorial
ms.prod: m365-security
ms.technology: m365d
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
ms.openlocfilehash: 056244562191389ee0991ef1040348ef5e6f82f7
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66015401"
---
# <a name="microsoft-365-security-for-business-decision-makers-bdms"></a>Microsoft 365 Security for Business Decision Makers (BDMs)

W tym artykule omówiono niektóre z najbardziej typowych scenariuszy zagrożeń i ataków, z którymi obecnie borykają się organizacje w swoich środowiskach Microsoft 365, oraz zalecane działania w celu ograniczenia tych zagrożeń. Chociaż Microsoft 365 oferuje szeroką gamę wstępnie skonfigurowanych funkcji zabezpieczeń, wymaga to również, aby klient wziął odpowiedzialność za zabezpieczanie własnych tożsamości, danych i urządzeń używanych do uzyskiwania dostępu do usług w chmurze. Te wskazówki zostały opracowane przez Kozeta Beam (Microsoft Cloud Security Architect) i Thiagaraj Sundararajan (starszy konsultant firmy Microsoft).

Ten artykuł jest uporządkowany według priorytetu pracy, począwszy od ochrony kont używanych do administrowania najbardziej krytycznymi usługami i zasobami, takimi jak dzierżawa, poczta e-mail i SharePoint. Zapewnia metodyczny sposób podejścia do zabezpieczeń i współdziała z następującym arkuszem kalkulacyjnym, dzięki czemu możesz śledzić swoje postępy z osobami biorącymi udział w projekcie i zespołami w całej organizacji: [Microsoft 365 zabezpieczenia arkusza kalkulacyjnego BDMs](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Microsoft-365-BDM-security-recommendations-spreadsheet.xlsx).

:::image type="content" source="../downloads/microsoft-365-bdm-security-recommendations-spreadsheet-thumb.png" alt-text="Przykład arkusza zaleceń dotyczących zabezpieczeń Microsoft 365 BDM" lightbox="../downloads/microsoft-365-bdm-security-recommendations-spreadsheet-thumb.png":::

Firma Microsoft udostępnia narzędzie Secure Score w dzierżawie, aby automatycznie analizować stan zabezpieczeń na podstawie zwykłych działań, przypisywać ocenę i udostępniać zalecenia dotyczące poprawy zabezpieczeń. Przed wykonaniem akcji zalecanych w tym artykule zanotuj bieżący wynik i zalecenia. Akcje zalecane w tym artykule zwiększą twój wynik. Celem nie jest osiągnięcie maksymalnego wyniku, ale świadomość możliwości ochrony środowiska w sposób, który nie ma negatywnego wpływu na produktywność użytkowników. Zobacz [Wskaźnik bezpieczeństwa firmy Microsoft](defender/microsoft-secure-score.md).

:::image type="content" source="../media/security/security-for-bdms-overview.png" alt-text="Kroki mające na celu ograniczenie ryzyka dla Twojej firmy" lightbox="../media/security/security-for-bdms-overview.png":::

Jeszcze jedna rzecz przed rozpoczęciem pracy. . . pamiętaj, aby [włączyć dziennik inspekcji](../compliance/search-the-audit-log-in-security-and-compliance.md). Te dane będą potrzebne później, w przypadku konieczności zbadania zdarzenia lub naruszenia zabezpieczeń.

## <a name="protect-privileged-accounts"></a>Ochrona kont uprzywilejowanych

W pierwszym kroku zalecamy zapewnienie, aby konta krytyczne w środowisku miały dodatkową warstwę ochrony, ponieważ te konta mają dostęp i uprawnienia do zarządzania usługami i zasobami o krytycznym znaczeniu, które mogą negatywnie wpłynąć na całą organizację, jeśli zostaną naruszone. Ochrona kont uprzywilejowanych jest jednym z najskuteczniejszych sposobów ochrony przed atakującym, który chce podnieść uprawnienia konta, którego zabezpieczenia zostały naruszone, do konta administracyjnego.

|Zalecenie|E3|E5|
|---|---|---|
|Wymuszanie uwierzytelniania wieloskładnikowego (MFA) dla wszystkich kont administracyjnych.|![zielony znacznik wyboru.](../media/green-check-mark.png)|![zielony znacznik wyboru.](../media/green-check-mark.png)|
|Zaimplementuj Azure Active Directory (Azure AD) Privileged Identity Management (PIM), aby zastosować uprzywilejowany dostęp just in time do zasobów Azure AD i platformy Azure. Możesz również dowiedzieć się, kto ma dostęp, i przejrzeć dostęp uprzywilejowany.||![zielony znacznik wyboru.](../media/green-check-mark.png)|
|Zaimplementuj zarządzanie dostępem uprzywilejowanym, aby zarządzać szczegółową kontrolą dostępu nad uprzywilejowanymi zadaniami administratora w Office 365.||![zielony znacznik wyboru.](../media/green-check-mark.png)|
|Konfigurowanie i używanie stacji roboczych z dostępem uprzywilejowanym (PAW) do administrowania usługami. Nie używaj tych samych stacji roboczych do przeglądania Internetu i sprawdzania poczty e-mail niezwiązanej z kontem administracyjnym.|!![zielony znacznik wyboru.](../media/green-check-mark.png)|![zielony znacznik wyboru.](../media/green-check-mark.png):::|

Na poniższym diagramie przedstawiono te możliwości.
:::image type="content" source="../media/m365-security-bdm-illustrations-privileged-accounts.png" alt-text="Zalecane możliwości ochrony kont uprzywilejowanych" lightbox="../media/m365-security-bdm-illustrations-privileged-accounts.png":::

Dodatkowe zalecenia:

- Upewnij się, że konta synchronizowane ze środowiska lokalnego nie mają przypisanych ról administratora dla usług w chmurze. Zapobiega to stosowaniu kont lokalnych przez osobę atakującą w celu uzyskania dostępu administracyjnego do usług w chmurze.
- Upewnij się, że konta usług nie mają przypisanych ról administratora. Te konta często nie są monitorowane i ustawiane przy użyciu haseł, które nie wygasają. Zacznij od upewnienia się, że konta usług AADConnect i ADFS nie są domyślnie administratorami globalnymi.
- Usuń licencje z kont administratorów. Jeśli nie istnieje konkretny przypadek użycia do przypisywania licencji do określonych kont administratorów, usuń licencje z tych kont.

## <a name="reduce-the-surface-of-attack"></a>Zmniejszanie obszaru podatnego na ataki

Następnym obszarem koncentracji uwagi jest zmniejszenie powierzchni ataku. Można to osiągnąć przy minimalnym wysiłku i wpływie na użytkowników i usługi. Dzięki zmniejszeniu obszaru podatnego na ataki osoby atakujące mają mniej sposobów na rozpoczęcie ataku na organizację.

Oto kilka przykładów:

- Wyłącz protokoły POP3, IMAP i SMTP. Większość nowoczesnych organizacji nie używa już tych starszych protokołów. Można je bezpiecznie wyłączyć i zezwolić na wyjątki tylko w razie potrzeby.
- Zmniejsz i zachowaj liczbę administratorów globalnych w dzierżawie do wymaganego bezwzględnego minimum. Zmniejsza to bezpośrednio obszar powierzchni ataku dla wszystkich aplikacji w chmurze.
- Wycofaj serwery i aplikacje, które nie są już używane w środowisku.
- Zaimplementuj proces wyłączania i usuwania kont, które nie są już używane.

## <a name="protect-against-known-threats"></a>Ochrona przed znanymi zagrożeniami

Znane zagrożenia obejmują złośliwe oprogramowanie, konta z naruszeniem zabezpieczeń i wyłudzanie informacji. Niektóre zabezpieczenia przed tymi zagrożeniami można szybko zaimplementować bez bezpośredniego wpływu na użytkowników, podczas gdy inne wymagają większego planowania i trenowania użytkowników.

|Zalecenie|E3|E5|
|---|---|---|
|**Skonfiguruj uwierzytelnianie wieloskładnikowe i użyj zalecanych zasad dostępu warunkowego, w tym zasad ryzyka logowania**. Firma Microsoft zaleca i przetestowała zestaw zasad, które współpracują ze sobą w celu ochrony wszystkich aplikacji w chmurze, w tym usług Office 365 i Microsoft 365. Zobacz [Konfiguracje tożsamości i dostępu do urządzeń](./office-365-security/microsoft-365-policies-configurations.md).||![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Wymagaj uwierzytelniania wieloskładnikowego dla wszystkich użytkowników**. Jeśli nie masz licencji wymaganej do zaimplementowania zalecanych zasad dostępu warunkowego, co najmniej wymaga uwierzytelniania wieloskładnikowego dla wszystkich użytkowników.|![zielony znacznik wyboru.](../media/green-check-mark.png)|![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Podnieś poziom ochrony przed złośliwym oprogramowaniem w wiadomości e-mail**. Środowisko Office 365 lub Microsoft 365 obejmuje ochronę przed złośliwym oprogramowaniem, ale można zwiększyć tę ochronę, blokując załączniki z typami plików, które są często używane w przypadku złośliwego oprogramowania.|![zielony znacznik wyboru.](../media/green-check-mark.png)|![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Ochrona poczty e-mail przed ukierunkowanymi atakami wyłudzania informacji**. Jeśli skonfigurowano co najmniej jedną domenę niestandardową dla środowiska Office 365 lub Microsoft 365, możesz skonfigurować docelową ochronę przed wyłudzaniem informacji. Ochrona przed wyłudzaniem informacji, będąca częścią Ochrona usługi Office 365 w usłudze Defender, może pomóc chronić organizację przed złośliwymi atakami phishingowymi opartymi na personifikacji i innymi atakami wyłudzania informacji. Jeśli domena niestandardowa nie została skonfigurowana, nie musisz tego robić.||![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Ochrona przed atakami ransomware w wiadomości e-mail**. Oprogramowanie wymuszające okup odbiera dostęp do danych przez szyfrowanie plików lub blokowanie ekranów komputerów. Następnie próbuje wyłudzać pieniądze od ofiar, prosząc o "okup", zwykle w formie kryptowalut, takich jak Bitcoin, w zamian za powrót dostępu do danych. Możesz pomóc w obronie przed oprogramowaniem wymuszającym okup, tworząc co najmniej jedną regułę przepływu poczty w celu blokowania rozszerzeń plików, które są często używane na potrzeby oprogramowania wymuszającego okup, lub aby ostrzegać użytkowników, którzy otrzymują te załączniki w wiadomości e-mail.|![zielony znacznik wyboru.](../media/green-check-mark.png)|![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Blokuj połączenia z krajów, z których nie robisz interesów**. Utwórz Azure AD zasad dostępu warunkowego, aby zablokować wszelkie połączenia pochodzące z tych krajów, skutecznie tworząc zaporę geograficzną wokół dzierżawy.||![zielony znacznik wyboru.](../media/green-check-mark.png)|

Na poniższym diagramie przedstawiono te możliwości.
:::image type="content" source="../media/m365-security-bdm-illustrations-known-threats.png" alt-text="Zalecane możliwości ochrony przed znanymi zagrożeniami" lightbox="../media/m365-security-bdm-illustrations-known-threats.png":::

## <a name="protect-against-unknown-threats"></a>Ochrona przed nieznanymi zagrożeniami

Po dodaniu dodatkowych zabezpieczeń do uprzywilejowanych kont i ochronie przed znanymi atakami należy zwrócić uwagę na ochronę przed nieznanymi zagrożeniami. Bardziej zdeterminowani i zaawansowani przeciwnicy używają innowacyjnych i nowych, nieznanych metod do atakowania organizacji. Dzięki ogromnej telemetrii danych firmy Microsoft zbieranej przez miliardy urządzeń, aplikacji i usług możemy wykonywać Ochrona usługi Office 365 w usłudze Defender na Windows, Office 365 i platformie Azure, aby zapobiegać atakom Zero-Day, korzystaniu ze środowisk piaskownicy i sprawdzaniu ważności przed zezwoleniem na dostęp do zawartości.

|Zalecenie|E3|E5|
|---|---|---|
|**Skonfiguruj Ochrona usługi Office 365 w usłudze Microsoft Defender**:<ul><li>załączniki Sejf</li><li>Bezpieczne linki</li><li>Bezpieczne załączniki dla programu SharePoint, usługi OneDrive i aplikacji Microsoft Teams</li><li>Ochrona przed personifikacją w zasadach ochrony przed wyłudzaniem informacji</li></ul>||![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Konfigurowanie możliwości Ochrona punktu końcowego w usłudze Microsoft Defender**:<ul><li>Program antywirusowy Windows Defender</li><li>Ochrona przed wykorzystywaniem</li><li>Zmniejszanie obszaru podatnego na ataki</li><li>Izolacja sprzętowa</li><li>Kontrolowany dostęp do folderu</li></ul>||![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Użyj Microsoft Defender for Cloud Apps**, aby odnaleźć aplikacje SaaS i zacząć używać analizy zachowań i wykrywania anomalii.||![zielony znacznik wyboru.](../media/green-check-mark.png)|

Na poniższym diagramie przedstawiono te możliwości.
:::image type="content" source="../media/m365-security-bdm-illustrations-unknown-threats.png" alt-text="Przykład możliwości oferowanych przez narzędzia do ochrony przed nieznanymi zagrożeniami" lightbox="../media/m365-security-bdm-illustrations-unknown-threats.png":::

Dodatkowe zalecenia:

- Zabezpieczanie komunikacji kanału partnerskiego, takiego jak wiadomości e-mail przy użyciu protokołu TLS.
- Otwórz Teams federacji tylko dla partnerów, z którą się komunikujesz.
- Nie należy dodawać domen nadawców, pojedynczych nadawców ani źródłowych adresów IP do listy dozwolonych, ponieważ umożliwia to pomijanie kontroli spamu i złośliwego oprogramowania — typowym rozwiązaniem w przypadku klientów jest dodawanie własnych zaakceptowanych domen lub wielu innych domen, w których problemy z przepływem poczty e-mail mogły być zgłaszane do listy dozwolonych. Nie należy dodawać domen na liście Filtrowanie spamu i połączeń, ponieważ potencjalnie pomija to wszystkie testy spamu.
- Włącz wychodzące powiadomienia o spamie — włącz powiadomienia o wychodzącym spamie na liście dystrybucyjnej wewnętrznie do zespołu pomocy technicznej lub administratora IT, aby zgłaszać, czy którykolwiek z użytkowników wewnętrznych wysyła wiadomości e-mail ze spamem na zewnątrz. Może to być wskaźnik naruszenia zabezpieczeń konta.
- Wyłącz zdalny program PowerShell dla wszystkich użytkowników — zdalny program PowerShell jest używany głównie przez administratorów do uzyskiwania dostępu do usług do celów administracyjnych lub programowego dostępu do interfejsu API. Zalecamy wyłączenie tej opcji dla użytkowników niebędących administratorami, aby uniknąć rekonesansu, chyba że mają oni wymaganie biznesowe, aby uzyskać do niej dostęp.
- Zablokuj dostęp do portalu zarządzania Microsoft Azure wszystkim spoza administratorów. Można to zrobić, tworząc regułę dostępu warunkowego, aby zablokować wszystkich użytkowników, z wyjątkiem administratorów.

## <a name="assume-breach"></a>Załóżmy, że naruszenie

Mimo że firma Microsoft podejmuje wszelkie możliwe środki w celu zapobiegania zagrożeniom i atakom, zalecamy zawsze pracę w ramach myślenia "Przyjmij naruszenie". Nawet jeśli atakującemu udało się wtargnąć do środowiska, musimy upewnić się, że nie może eksfiltrować danych lub informacji o tożsamości ze środowiska. Z tego powodu zalecamy włączenie ochrony przed wyciekami poufnych danych, takimi jak numery ubezpieczenia społecznego, numery kart kredytowych, inne dane osobowe i inne informacje poufne na poziomie organizacji.

|Zalecenie|E3|E5|
|---|---|---|
|**Przejrzyj i zoptymalizuj dostęp warunkowy i powiązane zasady, aby dopasować je do celów sieci zerowego zaufania**. Ochrona przed znanymi zagrożeniami obejmuje implementowanie zestawu [zalecanych zasad](./office-365-security/microsoft-365-policies-configurations.md). Przejrzyj implementację tych zasad, aby upewnić się, że chronisz swoje aplikacje i dane przed hakerami, którzy uzyskali dostęp do Sieci. Zalecane zasady ochrony aplikacji Intune dla Windows 10 umożliwiają Windows Information Protection (WIP). Funkcja WIP chroni przed przypadkowymi wyciekami danych organizacji za pośrednictwem aplikacji i usług, takich jak poczta e-mail, media społecznościowe i chmura publiczna.||![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Wyłącz przekazywanie zewnętrznych wiadomości e-mail**. Hakerzy uzyskujący dostęp do skrzynki pocztowej użytkownika mogą ukraść Twoją pocztę, ustawiając skrzynkę pocztową do automatycznego przekazywania wiadomości e-mail. Może się to zdarzyć nawet bez świadomości użytkownika. Możesz temu zapobiec, konfigurując regułę przepływu poczty.|![zielony znacznik wyboru.](../media/green-check-mark.png)|![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Wyłącz anonimowe udostępnianie kalendarza zewnętrznego**. Domyślnie zewnętrzne udostępnianie kalendarza anonimowego jest dozwolone. [Wyłącz udostępnianie kalendarza](/exchange/sharing/sharing-policies/modify-a-sharing-policy) , aby ograniczyć potencjalne przecieki poufnych informacji.|![zielony znacznik wyboru.](../media/green-check-mark.png)|![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Konfigurowanie zasad ochrony przed utratą danych dla danych poufnych**. Utwórz zasady ochrony przed utratą danych w usłudze Microsoft Purview, aby odnajdywać i chronić dane poufne, takie jak numery kart kredytowych, numery ubezpieczenia społecznego i numery kont bankowych. Microsoft 365 zawiera wiele wstępnie zdefiniowanych typów informacji poufnych, których można użyć w zasadach ochrony przed utratą danych. Możesz również utworzyć własne typy informacji poufnych dla danych poufnych, które są niestandardowe dla środowiska.|![zielony znacznik wyboru.](../media/green-check-mark.png)|![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Implementowanie zasad klasyfikacji danych i ochrony informacji**. Zaimplementuj etykiety poufności i użyj ich do klasyfikowania i stosowania ochrony danych poufnych. Te etykiety można również używać w zasadach ochrony przed utratą danych. Jeśli używasz etykiet usługi Azure Information Protection, zalecamy unikanie tworzenia nowych etykiet w innych centrach administracyjnych.||![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Ochrona danych w aplikacjach i usługach innych firm przy użyciu usługi Defender dla Chmury Apps**. Skonfiguruj zasady Defender dla Chmury Apps, aby chronić poufne informacje w aplikacjach innych firm w chmurze, takich jak Salesforce, Box lub Dropbox. Możesz użyć typów informacji poufnych i etykiet poufności utworzonych w zasadach Defender dla Chmury Apps i zastosować je w aplikacjach SaaS. <p> Microsoft Defender for Cloud Apps umożliwia wymuszanie szerokiego zakresu zautomatyzowanych procesów. Zasady można ustawić tak, aby zapewniały ciągłe skanowanie zgodności, prawne zadania zbierania elektronicznych materiałów dowodowych, DLP dla zawartości poufnej udostępnianej publicznie i nie tylko. Defender dla Chmury Aplikacje mogą monitorować dowolny typ pliku na podstawie ponad 20 filtrów metadanych (na przykład poziomu dostępu, typu pliku).||![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Użyj [Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/information-protection-in-windows-overview), aby określić, czy użytkownicy przechowują poufne informacje na swoich urządzeniach Windows**.||![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Użyj [skanera usługi AIP](/azure/information-protection/deploy-aip-scanner) , aby identyfikować i klasyfikować informacje między serwerami i udziałami plików**. Użyj narzędzia raportowania usługi AIP, aby wyświetlić wyniki i podjąć odpowiednie działania.||![zielony znacznik wyboru.](../media/green-check-mark.png)|

Na poniższym diagramie przedstawiono te możliwości.
:::image type="content" source="../media/m365-security-bdm-illustrations-assume-breach.png" alt-text="Funkcje zalecane do ochrony przed nieznanymi zagrożeniami" lightbox="../media/m365-security-bdm-illustrations-assume-breach.png":::

## <a name="continuous-monitoring-and-auditing"></a>Ciągłe monitorowanie i inspekcja

Ponadto ciągłe monitorowanie i inspekcja środowiska Microsoft 365 wraz z Windows i urządzeniami ma kluczowe znaczenie dla szybkiego wykrywania i korygowania wszelkich włamań. Narzędzia takie jak Wskaźnik bezpieczeństwa, portal Microsoft 365 Defender i zaawansowana analiza usługi Microsoft Intelligent Graph dostarczają nieocenionych informacji do dzierżawy i łączą ogromne ilości danych analizy zagrożeń i zabezpieczeń, aby zapewnić niezrównaną ochronę przed zagrożeniami i wykrywanie.

|Zalecenie|E3|E5|
|---|---|---|
|Upewnij się, że **dziennik inspekcji** jest włączony.|![zielony znacznik wyboru.](../media/green-check-mark.png)|![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Przejrzyj wskaźnik bezpieczeństwa co tydzień** — wskaźnik bezpieczeństwa to centralna lokalizacja umożliwiająca dostęp do stanu zabezpieczeń firmy i podjęcie akcji na podstawie zaleceń dotyczących wskaźnika bezpieczeństwa. Zaleca się wykonanie tego sprawdzania co tydzień.|![zielony znacznik wyboru.](../media/green-check-mark.png)|![zielony znacznik wyboru.](../media/green-check-mark.png)|
|Użyj **narzędzi Ochrona usługi Office 365 w usłudze Microsoft Defender**: <ul><li>Możliwości badania zagrożeń i reagowania na nie</li><li>Zautomatyzowane badanie i reagowanie</li></ul>||![zielony znacznik wyboru.](../media/green-check-mark.png)|
|Użyj **Ochrona punktu końcowego w usłudze Microsoft Defender**: <ul><li>[Wykrywanie i reagowanie dotyczące punktów końcowych](/windows/security/threat-protection/microsoft-defender-atp/overview-endpoint-detection-response)</li><li>Zautomatyzowane badanie i korygowanie Wskaźnik bezpieczeństwa</li><li>[Zaawansowane wyszukiwanie zagrożeń](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)</li></ul>||![zielony znacznik wyboru.](../media/green-check-mark.png)|
|Użyj **Microsoft Defender for Cloud Apps** do wykrywania nietypowych zachowań w aplikacjach w chmurze w celu identyfikowania oprogramowania wymuszającego okup, naruszeń zabezpieczeń użytkowników lub nieautoryzowanych aplikacji, analizowania użycia wysokiego ryzyka i automatycznego korygowania w celu ograniczenia ryzyka dla organizacji.||:::image type="content" source="../media/green-check-mark.png" alt-text="Przykład zielonego znacznika wyboru" lightbox="../media/green-check-mark.png":::|
|Użyj **usługi Microsoft Sentinel** lub bieżącego narzędzia SIEM, aby monitorować zagrożenia w całym środowisku.||![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Wdrażanie [Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp)** w celu monitorowania i ochrony przed zagrożeniami skierowanymi do środowiska lokalna usługa Active Directory.||![zielony znacznik wyboru.](../media/green-check-mark.png)|
|Użyj **Microsoft Defender dla Chmury**, aby monitorować zagrożenia w obciążeniach hybrydowych i chmurowych. Microsoft Defender dla Chmury obejmuje bezpłatną warstwę możliwości i warstwę standardową możliwości, za które są opłacane na podstawie godzin zasobów lub transakcji.

Na poniższym diagramie przedstawiono te możliwości.

:::image type="content" source="../media/m365-security-bdm-illustrations-monitoring-auditing.png" alt-text="Zalecane możliwości ciągłego monitorowania i inspekcji" lightbox="../media/m365-security-bdm-illustrations-monitoring-auditing.png":::

Najważniejsze zalecane akcje monitorowania:

- **Przegląd wskaźnika bezpieczeństwa firmy Microsoft co tydzień** — wskaźnik bezpieczeństwa to centralna lokalizacja umożliwiająca dostęp do stanu zabezpieczeń dzierżawy i podjęcie akcji na podstawie najważniejszych zaleceń. Zaleca się wykonanie tego sprawdzania co tydzień. Wskaźnik bezpieczeństwa obejmuje zalecenia z różnych Azure AD, Intune, Defender dla Chmury Apps i Ochrona punktu końcowego w usłudze Microsoft Defender, a także Office 365.
- **Co tydzień przejrzyj ryzykowne logowania** — co tydzień przejrzyj ryzykowne logowania za pomocą centrum administracyjnego Azure AD. Zalecany zestaw reguł tożsamości i dostępu do urządzeń zawiera zasady wymuszania zmiany hasła podczas ryzykownych logowań.
- **Co tydzień przejrzyj najważniejsze złośliwe oprogramowanie i fałszywych użytkowników** — użyj Eksploratora zagrożeń Ochrona usługi Office 365 w usłudze Microsoft Defender, aby przejrzeć najlepszych użytkowników, których dotyczy złośliwe oprogramowanie i phish, oraz dowiedzieć się, jaka jest główna przyczyna tego, dlaczego dotyczy to tych użytkowników.
