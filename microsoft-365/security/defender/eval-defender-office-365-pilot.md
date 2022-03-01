---
title: Pilotażowa usługa Microsoft Defender Office 365, skorzystaj z oceny w środowisku produkcyjnym
description: Procedura pilotażowa oceny dla grup aktywnych i istniejących użytkowników w celu poprawnego przetestowania funkcji usługi Microsoft Defender dla systemu Office 365.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: 05/25/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: how-to
ms.technology: m365d
ms.openlocfilehash: 456f5dae90f2a559e82599271f23bd5f3452ac12
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63013680"
---
# <a name="pilot-microsoft-defender-for-office-365"></a>Pilotażowa usługa Microsoft Defender dla Office 365

**Dotyczy:**
- Microsoft 365 Defender

Ten artykuł dotyczy [kroku 3 z 3](eval-defender-office-365-overview.md) w procesie konfigurowania środowiska oceny dla programu Microsoft Defender dla programu Office 365. Aby uzyskać więcej informacji na temat tego procesu, zobacz artykuł [z omówieniem](eval-defender-office-365-overview.md).

Aby skonfigurować i skonfigurować pilotaż programu Microsoft Defender dla systemu Windows, należy wykonać Office 365.

![Kroki tworzenia pilotażu programu Microsoft Defender dla Office 365.](../../media/defender/m365-defender-office-pilot.png)

- [Krok 1. Tworzenie grup pilotażowych](#step-1-create-pilot-groups)
- [Krok 2. Konfigurowanie ochrony](#step-2-configure-protection)
- [Krok 3. Wypróbuj możliwości — zapoznaj się z symulacją, monitorowaniem i metrykami](#step-3-try-out-capabilities--get-familiar-with-simulation-monitoring-and-metrics)

Podczas oceny usługi Microsoft Defender dla Office 365 można wybrać pilotaż konkretnych użytkowników przed włączeniem i rozpoczęciem wymuszania zasad dla całej organizacji. Tworzenie grup dystrybucyjnych może ułatwić zarządzanie procesami wdrażania. Można na przykład utworzyć grupy, takie jak *Defender for Office 365 Users* (Standard Protection), *Defender for Office 365 Users (* Ściśle chronić), *Defender for Office 365 Users (Użytkownicy* korzystający z programu Office 365 — niestandardowa ochrona) lub *Defender for Office 365 Users* (Wyjątki).

Być może nie wiadomo, dlaczego w tym celu używane są terminy "Standard" i "Strict", ale to się stanie jasne, gdy dowiesz się więcej o programie Defender dla programu Office 365 ustawień wstępnych zabezpieczeń. Nazewnictwo grup "niestandardowe" i "wyjątki" mówi same za siebie, jednak większość użytkowników powinna podlegać standardowym  i ścisłym *grupom* niestandardowym i grupom wyjątków, które będą gromadzić cenne dane dotyczące zarządzania ryzykiem.

## <a name="step-1-create-pilot-groups"></a>Krok 1. Tworzenie grup pilotażowych

Grupy dystrybucyjne można tworzyć i tworzyć oraz bezpośrednio Exchange Online lub synchronizować z lokalnej usługi Active Directory.

1. Logowanie do centrum Exchange administracyjnego przy użyciu konta, które otrzymało rolę Administrator adresata lub do których zostały delegowane uprawnienia zarządzania grupą.
2. W menu nawigacji rozwiń pozycję **Adresaci** i wybierz pozycję <a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank">**Grupy**</a>.

   :::image type="content" source="../../media/mdo-eval/1_mdo-eval-pilot.png" alt-text="Exchange w menu nawigacji (szybkie uruchamianie) ze strzałką wskazującą pozycję Grupy. Kliknij pozycję Grupy.":::

3. Na pulpicie nawigacyjnym Grupy wybierz pozycję "Dodaj grupę".

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-pilot-add-group.png" alt-text="Dodaj grupy w panelu Grupy.":::

4. W przypadku typu grupy wybierz pozycję *Dystrybucja* i kliknij przycisk Dalej.

   :::image type="content" source="../../media/mdo-eval/3-mdo-eval-pilot-group-type.png" alt-text="Wybierz tutaj typ grupy dystrybucyjnej.":::

5. Nadaj grupie nazwę i opis, a następnie kliknij przycisk Dalej.

   :::image type="content" source="../../media/mdo-eval/4_mdo-eval-pilot-set-up-basics.png" alt-text="Nadaj nazwę i opisz grupę.":::

## <a name="step-2-configure-protection"></a>Krok 2. Konfigurowanie ochrony

Niektóre funkcje w programie Defender Office 365 są domyślnie skonfigurowane i włączone, ale operacje zabezpieczeń mogą wymagać podwyżsowania poziomu ochrony z poziomu domyślnego.

Niektóre funkcje nie *są jeszcze* skonfigurowane. Dostępne są trzy opcje konfigurowania ochrony:

- **Automatyczne przypisywanie wstępnie ustawionych** zasad [zabezpieczeń — wstępnie](../office-365-security/preset-security-policies.md) ustawione zasady zabezpieczeń są udostępniane jako metoda szybkiego przypisywania jednolitego poziomu ochrony dla wszystkich funkcji. Do wyboru są standardowe ***_ lub _*_ścisłe_**. Dobrym rozwiązaniem jest rozpoczęcie od wstępnie ustawionych zasad zabezpieczeń, a następnie dostosowanie zasad w celu dowiedzenia się więcej o możliwościach i własnym unikatowym środowisku zagrożeń. Zaletą tego jest to, że chronisz grupy użytkowników tak szybko, jak to możliwe, oraz możliwość późniejszego dostosowania ochrony. (Ta metoda jest zalecana).
- **Ręczne konfigurowanie ochrony według** planu bazowego — jeśli wolisz samodzielnie skonfigurować środowisko, możesz szybko osiągnąć plan bazowy ochrony, korzystając z porad w tece Ochrona [przed zagrożeniami](../office-365-security/protect-against-threats.md). Ta metoda pozwala uzyskać więcej informacji na temat ustawień, które można konfigurować. Oczywiście możesz dostosować te zasady później.
- **Konfigurowanie *niestandardowych* zasad ochrony** — w ramach oceny można również tworzyć i przypisywać niestandardowe zasady ochrony. Przed rozpoczęciem dostosowywania zasad należy zrozumieć pierwszeństwo stosowania i wymuszania tych zasad ochrony. W celu zdefiniowania zasad zabezpieczeń dla linków programu Sejf i załączników w celu określenia ustawień wstępnych należy utworzyć pewne zasady nawet w przypadku stosowania Sejf zabezpieczeń.

> [!IMPORTANT]
> **Jeśli musisz skonfigurować** niestandardowe zasady ochrony, sprawdź wartości, które są definicjami zabezpieczeń standardowych i ścisłych:  Zalecane ustawienia usług *[EOP i Microsoft Defender](../office-365-security/recommended-settings-for-eop-and-office365.md)* w Office 365 zabezpieczeń. Na liście znajdują się również wartości domyślne widoczne przed rozpoczęciem jakiejkolwiek konfiguracji. Zachowaj arkusz kalkulacyjny miejsca, w którym twoja kompilacja niestandardowa się dechyguje.

### <a name="assign-preset-security-policies"></a>Przypisywanie wstępnie ustawionych zasad zabezpieczeń

Zaleca się rozpoczęcie od zalecanych zasad planu bazowego  podczas oceniania obiektu MDO, a następnie uściślianie ich w razie potrzeby w trakcie okresu oceny.

Zalecane usługi EOP i Defender można szybko włączyć Office 365 ochrony i przypisać je określonym użytkownikom pilotażowym lub zdefiniowanym grupom w ramach oceny. Wstępnie ustawione zasady oferują szablon **standardowej** ochrony według planu bazowego lub  bardziej rygorystyczny szablon ścisłej ochrony, który można przypisać niezależnie lub razem.

Poniżej znajduje się artykuł Wstępnie ustawione [zasady zabezpieczeń w usługach EOP i Microsoft Defender Office 365](../office-365-security/preset-security-policies.md) z instrukcjami.

1. Zaloguj się do Microsoft 365 dzierżawy. Korzystanie z konta z dostępem do portalu Microsoft 365 Defender, dodanego do roli Zarządzanie organizacją w programie Office 365 lub roli Administratora zabezpieczeń w programie Microsoft 365.
2. Z menu nawigacji wybierz polecenie *Zasady i reguły & w* obszarze Poczta e-mail & współpracy.

   :::image type="content" source="../../media/mdo-eval/5_mdo-eval-pilot-policies.png" alt-text="W obszarze &-mail w panelu nawigacji kliknij pozycję Zasady & reguły.":::

3. Na pulpicie nawigacyjnym & zasad kliknij pozycję *Zasady zagrożeń*.

   :::image type="content" source="../../media/mdo-eval/6-mdo-eval-pilot-threat-policies.png" alt-text="a.":::

4. W portalu Microsoft 365 Defender rozwiń pozycję Zarządzanie zagrożeniami z menu nawigacji, a następnie wybierz pozycję Zasady z podmenu.
5. Na pulpicie nawigacyjnym zasad kliknij pozycję *Wstępnie ustawione zasady zabezpieczeń*.

   :::image type="content" source="../../media/mdo-eval/7-mdo-eval-pilot-template-policies.png" alt-text="Kliknij kafelek Wstępnie ustawione zasady zabezpieczeń.":::

6. Kliknij *pozycję Edytuj* , aby skonfigurować i przypisać zasady Standardowe i/lub Ścisłe.

   :::image type="content" source="../../media/mdo-eval/8-mdo-eval-pilot-preset.png" alt-text="W panelu Wstępnie ustawione zasady zabezpieczeń kliknij pozycję Edytuj.":::

7. Dodaj warunki, aby zastosować ochronę podstawową ***EOP** _ do określonych użytkowników pilotażowych lub grup użytkowników (w razie potrzeby), a następnie wybierz pozycję _Next*, aby kontynuować.

   Na przykład warunek "Defender for Office 365" do oceny pilotażowej można zastosować, jeśli adresaci są członkami zdefiniowanej grupy Usługi Defender dla usługi *Office 365 Standard Protection*, a następnie zarządzać nimi, po prostu dodając konta do grupy lub usuwając z nich konto.

   :::image type="content" source="../../media/mdo-eval/9-mdo-eval-pilot-eop-protections.png" alt-text="Dodaj warunki wymagane do zastosowania poziomu zabezpieczeń programu EOP do grupy pilotażowej.":::

8. Dodaj warunki, aby w razie potrzeby zastosować ochronę podstawową ***MDO** _ do konkretnych użytkowników pilotażowych lub grup użytkowników. Kliknij przycisk _Next*, aby kontynuować.

   Na przykład warunek "Defender for Office 365" do oceny pilotażowej można zastosować, jeśli adresaci są członkami zdefiniowanej grupy *Usługi Defender dla usługi Office 365 Standard Protection*, a następnie zarządzać nimi, po prostu dodając/usuwając konta za pośrednictwem tej grupy.

   :::image type="content" source="../../media/mdo-eval/10-mdo-eval-pilot-mdo-protections.png" alt-text="Dodaj warunki wymagane do zastosowania usługi Defender Office 365 poziomu zabezpieczeń do grupy pilotażowej.":::

9. Przejrzyj i potwierdź zmiany dotyczące przypisywania wstępnie ustawionych zasad zabezpieczeń.
10. Wstępnie ustawione zasady ochrony można zarządzać (ponownie skonfigurować, zastosować ponownie, wyłączyć itp.), wracając do portalu Microsoft 365 Defender > Policies & Rules > Threat Policies > i klikając kafelek Wstępnie ustawione zasady zabezpieczeń.

### <a name="configure-custom-protection-policies"></a>Konfigurowanie niestandardowych zasad ochrony

Wstępnie zdefiniowane szablony zasad *grupy Standard* lub *Strict* Defender for Office 365 zapewniają użytkownikom pilotażowym zalecaną ochronę podstawową. W ramach oceny można jednak również tworzyć i przypisywać niestandardowe zasady ochrony.

Ważne *jest, aby* wiedzieć o pierwszeństwie stosowania i wymuszania tych zasad ochrony, ponieważ jest to kolejność i pierwszeństwo ochrony poczty e-mail — [Office 365 wyjaśniono](../office-365-security/how-policies-and-protections-are-combined.md).

W poniższej tabeli przedstawiono odwołania i dodatkowe wskazówki dotyczące konfigurowania i przypisywania niestandardowych zasad ochrony:

<br>

****

|Zasady|Opis|Odwołanie|
|:---:|---|---|
|Filtrowanie połączeń|Zidentyfikuj dobre lub złe źródłowe serwery poczty e-mail na pomocą adresów IP.|[Konfigurowanie domyślnych zasad filtru połączenia w u usługi EOP](../office-365-security/configure-the-connection-filter-policy.md)|
|Ochrona przed złośliwym oprogramowaniem|Chroń użytkowników przed złośliwym oprogramowaniem poczty e-mail, w tym jakie działania należy podjąć i kto może powiadamiać w przypadku wykrycia złośliwego oprogramowania.|[Konfigurowanie zasad ochrony przed złośliwym oprogramowaniem w u usługi EOP](../office-365-security/configure-anti-malware-policies.md)|
|Ochrona przed fałszowaniem|Chroń użytkowników przed próbami fałszowania przy użyciu analizy fałszowania i informacji sfałszowanych.|[Konfigurowanie analizy przed fałszerami w programie Defender dla Office 365](../office-365-security/learn-about-spoof-intelligence.md)|
|Ochrona przed spamem|Chroń użytkowników przed spamem wiadomości e-mail, w tym jakie działania należy podjąć w przypadku wykrycia spamu.|[Konfigurowanie zasad ochrony przed spamem w programie Defender dla Office 365](../office-365-security/configure-your-spam-filter-policies.md)|
|Ochrona przed wyłudzaniem informacji|Ochrona użytkowników przed atakami wyłudzających informacje i konfigurowanie porad dotyczących bezpieczeństwa w przypadku podejrzanych wiadomości|[Konfigurowanie zasad ochrony przed wyłudzaniem informacji w programie Defender dla Office 365](../office-365-security/configure-mdo-anti-phishing-policies.md)|
|Sejf załączników|Chroń użytkowników przed złośliwą zawartością załączników i plików w SharePoint, OneDrive i innych Teams.|[Konfigurowanie bezpiecznych zasad załączników w programie Defender dla Office 365](../office-365-security/set-up-safe-attachments-policies.md)|
|Bezpieczne linki|Chroń użytkowników przed otwieraniem i udostępnianiem złośliwych linków w wiadomościach e-mail Office aplikacjach klasycznych.|[Konfigurowanie bezpiecznych zasad linków w programie Defender dla Office 365](../office-365-security/set-up-safe-links-policies.md)|
|

## <a name="step-3-try-out-capabilities--get-familiar-with-simulation-monitoring-and-metrics"></a>Krok 3. Wypróbuj możliwości — zapoznaj się z symulacją, monitorowaniem i metrykami

Po skonfigurowaniu i skonfigurowaniu pilotażu warto zapoznać się z narzędziami do raportowania, monitorowania i ataków, które są unikatowe dla programu Microsoft Defender dla systemu Microsoft 365.

<br>

****

|Funkcja|Opis|Więcej informacji|
|---|---|---|
|Eksplorator zagrożeń|Eksplorator zagrożeń to zaawansowane narzędzie w czasie rzeczywistym, które pomaga zespołom operacji zabezpieczeń badać zagrożenia i reagować na nie oraz wyświetla informacje o podejrzanym złośliwym oprogramowaniu i wyłudzeniu informacji w wiadomościach e-mail i plikach w programie Office 365, a także o innych zagrożeniach bezpieczeństwa i zagrożeniach dla organizacji.|[Widoki w Eksploratorze zagrożeń i wykrywania w czasie rzeczywistym](../office-365-security/threat-explorer-views.md)|
|Atak zbędny|Za pomocą szkolenia z symefikacyjnego ataków w portalu Microsoft 365 Defender można uruchamiać realistycznych scenariuszy ataków w organizacji, które ułatwiają identyfikowanie i znajdowanie narażonych użytkowników, zanim rzeczywisty atak będzie oddziaływał na Twoje środowisko.|[Wprowadzenie do korzystania ze szkolenia symulacyjnego w zakresie ataków](../office-365-security/attack-simulation-training-get-started.md)|
|Pulpit nawigacyjny Raporty|W lewym menu nawigacji kliknij pozycję Raporty i rozwiń nagłówek Poczta & współpracy. Raporty współpracy usługi e-mail & służą do wykrywania trendów zabezpieczeń, z których niektóre pozwalają podjąć działania (za pomocą przycisków, takich jak "Przejdź do przesyłania"), a także innych, które pokazują trendy, takie jak podsumowanie stanu przepływu poczty, najlepsze złośliwe oprogramowanie, wykrywanie fałszowania, naruszoni użytkownicy, opóźnienie poczty, linki programu Sejf i raporty załączników programu Sejf. Te metryki są generowane automatycznie.|[Wyświetlanie raportów](../office-365-security/view-email-security-reports.md)|
|

## <a name="next-steps"></a>Następne kroki

[Szacowanie programu Microsoft Defender pod celu punktu końcowego](eval-defender-endpoint-overview.md)

Wróć do przeglądu [szacowania programu Microsoft Defender dla programu Office 365](eval-defender-office-365-overview.md)

Wróć do przeglądu projektów [oceniania i Microsoft 365 Defender](eval-overview.md)
