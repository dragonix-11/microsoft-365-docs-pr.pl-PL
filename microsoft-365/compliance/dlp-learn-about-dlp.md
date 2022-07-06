---
title: Dowiedz się więcej o ochronie przed utratą danych
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Dowiedz się, jak chronić poufne informacje przy użyciu zasad i narzędzi ochrony przed utratą danych w usłudze Microsoft Purview i zapoznać się z cyklem życia DLP.
ms.openlocfilehash: 2bcc82f0609f617219d626f8180e7f4c9df51060
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641915"
---
# <a name="learn-about-data-loss-prevention"></a>Dowiedz się więcej o ochronie przed utratą danych

Organizacje mają pod kontrolą poufne informacje, takie jak dane finansowe, dane zastrzeżone, numery kart kredytowych, dokumentacja kondycji lub numery ubezpieczenia społecznego. Aby chronić te poufne dane i zmniejszyć ryzyko, potrzebują sposobu, aby uniemożliwić użytkownikom niewłaściwe udostępnianie ich osobom, które nie powinny ich mieć. Ta praktyka jest nazywana zapobieganiem utracie danych (DLP).

W usłudze Microsoft Purview można zaimplementować ochronę przed utratą danych, definiując i stosując zasady DLP. Za pomocą zasad DLP można identyfikować, monitorować i automatycznie chronić poufne elementy w różnych obszarach:

- Usługi platformy Microsoft 365, takie jak Teams, Exchange, SharePoint i OneDrive
- Aplikacje pakietu Office, takie jak Word, Excel i PowerPoint
- punkty końcowe Windows 10, Windows 11 i macOS (Catalina 10.15 i nowsze)
- aplikacje w chmurze spoza firmy Microsoft
- lokalnych udziałów plików i lokalnego programu SharePoint.

DLP wykrywa poufne elementy przy użyciu głębokiej analizy zawartości, a nie tylko przez proste skanowanie tekstu. Zawartość jest analizowana pod kątem podstawowych dopasowań danych do słów kluczowych, oceny wyrażeń regularnych, wewnętrznej weryfikacji funkcji i pomocniczych dopasowań danych znajdujących się w pobliżu podstawowego dopasowania danych. Poza tym DLP używa również algorytmów uczenia maszynowego i innych metod do wykrywania zawartości zgodnej z zasadami DLP.

## <a name="dlp-is-part-of-the-larger-microsoft-purview-offering"></a>DLP jest częścią większej oferty usługi Microsoft Purview

DLP to tylko jedno z narzędzi usługi Microsoft Purview, które ułatwia ochronę poufnych elementów wszędzie tam, gdzie mieszkają lub podróżują. Należy zrozumieć inne narzędzia w zestawie narzędzi Usługi Microsoft Purview, sposób ich wzajemnej współpracy i lepszą współpracę.  Zobacz [Narzędzia usługi Microsoft Purview](protect-information.md) , aby dowiedzieć się więcej o procesie ochrony informacji.

## <a name="protective-actions-of-dlp-policies"></a>Działania ochronne zasad DLP

Zasady DLP to sposób monitorowania działań wykonywanych przez użytkowników w przypadku poufnych elementów magazynowanych, poufnych elementów przesyłanych lub poufnych elementów w użyciu i podejmowania działań ochronnych. Na przykład gdy użytkownik próbuje podjąć niedozwoloną akcję, taką jak kopiowanie poufnego elementu do niezatwierdzone miejsce lub udostępnianie informacji medycznych w wiadomości e-mail lub innych warunkach określonych w zasadach, DLP może:

- wyświetl wyskakujące wskazówki dotyczące zasad dla użytkownika, który ostrzega użytkownika, że może on próbować niewłaściwie udostępnić poufny element
- zablokuj udostępnianie i za pośrednictwem porady dotyczącej zasad zezwalaj użytkownikowi na zastąpienie bloku i przechwytywanie uzasadnienia użytkowników
- blokowanie udostępniania bez opcji zastąpienia
- W przypadku danych magazynowanych poufne elementy można zablokować i przenieść do bezpiecznej lokalizacji kwarantanny
- w przypadku czatu w usłudze Teams poufne informacje nie będą wyświetlane

Wszystkie monitorowane działania DLP są domyślnie rejestrowane w [dzienniku inspekcji platformy Microsoft 365](search-the-audit-log-in-security-and-compliance.md) i kierowane do [Eksploratora działań](data-classification-activity-explorer.md). Gdy użytkownik wykonuje akcję spełniającą kryteria zasad DLP i masz skonfigurowane alerty, usługa DLP udostępnia alerty na [pulpicie nawigacyjnym zarządzania alertami DLP](dlp-configure-view-alerts-policies.md).

## <a name="dlp-lifecycle"></a>Cykl życia DLP

Implementacja DLP zazwyczaj jest zgodna z tymi głównymi fazami.

- [Zaplanuj DLP](#plan-for-dlp)
- [Przygotowanie do DLP](#prepare-for-dlp)
- [Wdrażanie zasad w środowisku produkcyjnym](#deploy-your-policies-in-production)


<!--ADD DIAGRAM OF THE DLP LIFECYCLE WORK ON WITH MAS-->

### <a name="plan-for-dlp"></a>Zaplanuj DLP

Monitorowanie i ochrona DLP są natywne dla aplikacji używanych codziennie przez użytkowników. Pomaga to chronić poufne elementy organizacji przed ryzykownym działaniem, nawet jeśli użytkownicy nie są przyzwyczajeni do myślenia i praktyk zapobiegania utracie danych. Jeśli Twoja organizacja i użytkownicy dopiero zaczynają korzystać z praktyk ochrony przed utratą danych, wdrożenie DLP może wymagać zmiany procesów biznesowych i nastąpi zmiana kultury dla użytkowników. Jednak dzięki prawidłowemu planowaniu, testowaniu i dostrajaniu zasady DLP będą chronić poufne elementy przy jednoczesnym zminimalizowaniu wszelkich potencjalnych zakłóceń procesów biznesowych.

**Planowanie technologii dla DLP**

Należy pamiętać, że DLP jako technologia może monitorować i chronić dane magazynowane, dane używane i dane w ruchu na urządzeniach z usługami Microsoft 365, Windows 10, Windows 11 i macOS (Catalina 10.15 lub nowszym), lokalnych udziałach plików i lokalnym programie SharePoint. Istnieją implikacje dotyczące planowania dla różnych lokalizacji, typu danych, które chcesz monitorować i chronić, oraz akcji, które należy wykonać w przypadku dopasowania zasad.

**Planowanie procesów biznesowych dla DLP**

Zasady DLP mogą blokować zabronione działania, takie jak niewłaściwe udostępnianie informacji poufnych za pośrednictwem poczty e-mail. Podczas planowania zasad DLP należy zidentyfikować procesy biznesowe, które dotykają poufnych elementów. Właściciele procesów biznesowych mogą pomóc w zidentyfikowaniu odpowiednich zachowań użytkowników, które powinny być dozwolone, i nieodpowiednich zachowań użytkowników, przed które powinny być chronione. Należy zaplanować zasady i wdrożyć je w trybie testowym, a następnie najpierw ocenić ich wpływ za pośrednictwem [Eksploratora aktywności](data-classification-activity-explorer.md) przed zastosowaniem ich w bardziej restrykcyjnych trybach.

**Planowanie kultury organizacyjnej dla DLP**

Pomyślna implementacja DLP jest tak samo zależna od trenowania i aklimatyzacji użytkowników do praktyk zapobiegania utracie danych, jak i od dobrze zaplanowanych i dostosowanych zasad. Ponieważ użytkownicy są bardzo zaangażowani, należy również zaplanować szkolenia dla nich. Możesz strategicznie używać wskazówek dotyczących zasad, aby zwiększyć świadomość użytkowników przed zmianą wymuszania zasad z trybu testowego na bardziej restrykcyjne.

<!--For more information on planning for DLP, including suggestions for deployment based on your needs and resources, see [Planning for data loss prevention](dlp-plan-for-dlp.md).-->

### <a name="prepare-for-dlp"></a>Przygotowanie do DLP

Zasady DLP można stosować do danych magazynowanych, używanych danych i danych w ruchu w lokalizacjach, takich jak:

- Exchange Online e-mail
- Witryny usługi SharePoint Online
- Konta usługi OneDrive
- Wiadomości na czacie i kanale w usłudze Teams
- Microsoft Defender for Cloud Apps
- urządzenia Windows 10, Windows 11 i macOS (Catalina 10.15 i nowsze)
- Repozytoria lokalne
- Witryny usługi PowerBI

Każdy z nich ma inne wymagania wstępne. Poufne elementy w niektórych lokalizacjach, takie jak exchange online, mogą być objęte parasolem DLP, konfigurując zasady, które mają zastosowanie do nich. Inne, takie jak lokalne repozytoria plików, wymagają wdrożenia skanera usługi Azure Information Protection (AIP). Przed aktywowaniem jakichkolwiek akcji blokujących należy przygotować środowisko, tworzyć wersje robocze zasad kodu i dokładnie je przetestować.

### <a name="deploy-your-policies-in-production"></a>Wdrażanie zasad w środowisku produkcyjnym

#### <a name="design-your-policies"></a>Projektowanie zasad

Zacznij od zdefiniowania celów kontroli i sposobu ich stosowania w poszczególnych obciążeniach. Utwórz wersje zasad, które będą odzwierciedlać Twoje cele. Możesz zacząć od jednego obciążenia naraz lub dla wszystkich obciążeń — nie ma jeszcze żadnego wpływu.

#### <a name="implement-policy-in-test-mode"></a>Implementowanie zasad w trybie testowym

Oceń wpływ kontrolek, implementując je przy użyciu zasad DLP w trybie testowym. Zasady można zastosować do wszystkich obciążeń w trybie testowym, aby uzyskać pełną szerokość wyników, ale w razie potrzeby możesz zacząć od jednego obciążenia.

#### <a name="monitor-outcomes-and-fine-tune-the-policy"></a>Monitorowanie wyników i dostosowywanie zasad

W trybie testowym monitoruj wyniki zasad i dostosuj je tak, aby spełniał cele kontroli, zapewniając jednocześnie, że nie wpływa to niekorzystnie lub nieumyślnie na prawidłowe przepływy pracy i produktywność użytkowników. Oto kilka przykładów elementów, które należy dostosować:

- dostosowywanie lokalizacji i osób/miejsc znajdujących się w zakresie lub poza jego zakresem
- dostrojenie warunków i wyjątków, które są używane do określania, czy element i co się z nim robi, jest zgodne z zasadami
- definicja informacji poufnych/s
- akcje
- poziom ograniczeń
- dodawanie nowych kontrolek
- dodawanie nowych osób
- dodawanie nowych aplikacji z ograniczeniami
- dodawanie nowych witryn z ograniczeniami

> [!NOTE]
> _Zatrzymanie przetwarzania większej liczby reguł_ nie działa w trybie testowym, nawet jeśli jest włączone.

#### <a name="enable-the-control-and-tune-your-policies"></a>Włączanie kontrolki i dostosowywanie zasad

Gdy zasady spełnią wszystkie twoje cele, włącz je. Kontynuuj monitorowanie wyników aplikacji zasad i dostrajanie w razie potrzeby. 

> [!NOTE]
> Ogólnie rzecz biorąc, zasady obowiązują około godziny po włączeniu.

<!--See, LINK TO topic for SLAs for location specific  details-->

## <a name="dlp-policy-configuration-overview"></a>Omówienie konfiguracji zasad DLP

Możesz elastycznie tworzyć i konfigurować zasady DLP. Możesz zacząć od wstępnie zdefiniowanego szablonu i utworzyć zasady za pomocą kilku kliknięć lub zaprojektować własne od podstaw. Niezależnie od wybranej opcji wszystkie zasady DLP wymagają od Ciebie tych samych informacji.

1. **Wybierz, co chcesz monitorować** — DLP zawiera wiele wstępnie zdefiniowanych szablonów zasad, które ułatwiają rozpoczęcie pracy lub można utworzyć zasady niestandardowe.
    - Wstępnie zdefiniowany szablon zasad: dane finansowe, dane medyczne i zdrowotne, dane dotyczące prywatności dla różnych krajów i regionów.
    - Zasady niestandardowe, które używają dostępnych typów informacji poufnych, etykiet przechowywania i etykiet poufności.
2. **Wybierz lokalizację, którą chcesz monitorować** — wybierasz co najmniej jedną lokalizację, którą chcesz monitorować pod kątem informacji poufnych. Możesz monitorować:

Lokalizacji | include/exclude by|
|---------|---------|
|Poczta e-mail programu Exchange| grupy dystrybucyjne|
|Witryny programu SharePoint |Witryn |
|Konta usługi OneDrive |konta lub grupy dystrybucyjne |
|Wiadomości na czacie i kanale w usłudze Teams |konto lub grupa dystrybucyjna |
|urządzenia Windows 10, Windows 11 i macOS (Catalina 10.15 i nowsze) |użytkownik lub grupa |
|Microsoft Cloud App Security |Wystąpienie |
|Repozytoria lokalne| ścieżka pliku repozytorium|

3. **Wybierz warunki, które muszą być dopasowane do zasad, które mają być stosowane do elementu** — możesz zaakceptować wstępnie skonfigurowane warunki lub zdefiniować warunki niestandardowe. Oto kilka przykładów:

- element zawiera określony rodzaj poufnych informacji używanych w określonym kontekście. Na przykład 95 numerów ubezpieczenia społecznego wysyłanych e-mailem do adresata spoza organizacji.
- element ma określoną etykietę poufności
- element z informacjami poufnymi jest udostępniany wewnętrznie lub zewnętrznie

4. **Wybierz akcję do wykonania po spełnieniu warunków zasad** — akcje zależą od lokalizacji, w której odbywa się działanie.  Oto kilka przykładów:

- SharePoint/Exchange/OneDrive: blokuj osobom spoza organizacji dostęp do zawartości. Pokaż użytkownikowi poradę i wyślij mu powiadomienie e-mail z informacją o tym, że podejmuje on akcję, która jest zabroniona przez zasady DLP.
- Czat i kanał usługi Teams: blokowanie udostępniania poufnych informacji w czacie lub kanale
- Windows 10, Windows 11 i macOS (Catalina 10.15 lub nowsze) Urządzenia: Inspekcja lub ograniczanie kopiowania poufnego elementu na wymienne urządzenie USB
- Aplikacje pakietu Office: pokaż wyskakujące okienko informujące użytkownika, że angażuje się w ryzykowne zachowanie i blokuje lub blokuje, ale zezwala na zastępowanie.
- Lokalne udziały plików: przenieś plik z miejsca przechowywania do folderu kwarantanny

> [!NOTE]
> Warunki i akcje do wykonania są definiowane w obiekcie o nazwie Reguła.

<!--## Create a DLP policy

All DLP policies are created and maintained in the Microsoft Purview center. See, INSERT LINK TO ARTICLE THAT WILL START WALKING THEM THROUGH THE POLICY CREATION PROCEDURES for more information.-->

Po utworzeniu zasad DLP w Centrum zgodności są one przechowywane w centralnym magazynie zasad, a następnie synchronizowane z różnymi źródłami zawartości, w tym:

- Exchange Online, a stamtąd do Outlook w sieci Web i Outlooka.
- OneDrive dla Firm witryn.
- Witryny usługi SharePoint Online.
- Programy klasyczne pakietu Office (Excel, PowerPoint i Word).
- Kanały i wiadomości czatu w usłudze Microsoft Teams.

Po zsynchronizowanym z odpowiednimi lokalizacjami zasady zaczynają oceniać zawartość i wymuszać akcje.

## <a name="viewing-policy-application-results"></a>Wyświetlanie wyników aplikacji zasad

DLP raportuje ogromną ilość informacji w usłudze Microsoft Purview z monitorowania, dopasowań zasad i akcji oraz działań użytkowników. Musisz korzystać z tych informacji i działać na nich, aby dostosować zasady i klasyfikować akcje podejmowane w przypadku poufnych elementów. Dane telemetryczne najpierw trafiają do [portal zgodności Microsoft Purview Dzienniki inspekcji](search-the-audit-log-in-security-and-compliance.md#search-the-audit-log-in-the-compliance-portal), są przetwarzane i trafiają do różnych narzędzi raportowania. Każde narzędzie raportowania ma inny cel.

### <a name="dlp-alerts-dashboard"></a>Pulpit nawigacyjny alertów DLP

Gdy DLP podejmuje akcję dotyczącą elementu poufnego, możesz otrzymać powiadomienie o tej akcji za pośrednictwem konfigurowalnego alertu. Zamiast piętrzyć się te alerty w skrzynce pocztowej, aby można było je przesiewać, centrum zgodności udostępnia je na [pulpicie nawigacyjnym zarządzania alertami DLP](dlp-configure-view-alerts-policies.md). Pulpit nawigacyjny alertów DLP służy do konfigurowania alertów, przeglądania ich, klasyfikowania ich i śledzenia rozwiązywania alertów DLP. Oto przykład alertów generowanych przez dopasowania zasad i działania z Windows 10 urządzeń.

> [!div class="mx-imgBorder"]
> ![Informacje o alertach.](../media/Alert-info-1.png)

Możesz również wyświetlić szczegóły skojarzonego zdarzenia z bogatymi metadanymi na tym samym pulpicie nawigacyjnym

> [!div class="mx-imgBorder"]
> ![informacje o zdarzeniu.](../media/Event-info-1.png)

### <a name="reports"></a>Raporty

[Raporty DLP](view-the-dlp-reports.md#view-the-reports-for-data-loss-prevention) pokazują szerokie trendy w czasie i dają szczegółowe informacje na temat:

- **Dopasowania zasad DLP** w czasie i filtrowanie według zakresu dat, lokalizacji, zasad lub akcji
- **Dopasowania zdarzeń DLP** również pokazują dopasowania w czasie, ale są przestawne na elementach, a nie na regułach zasad.
- **Wyniki fałszywie dodatnie i przesłonięcia DLP** pokazują liczbę wyników fałszywie dodatnich i, jeśli zostały skonfigurowane, przesłonięcia użytkowników wraz z uzasadnieniem użytkownika.

### <a name="dlp-activity-explorer"></a>Eksplorator działań DLP

Karta Eksplorator działań na stronie DLP ma wstępnie ustawiony filtr *działania* na *wartość DLPRuleMatch*. To narzędzie służy do przeglądania działań związanych z zawartością, która zawiera informacje poufne lub ma zastosowane etykiety, takie jak etykiety, które zostały zmienione, pliki zostały zmodyfikowane i dopasowane do reguły.

![zrzut ekranu przedstawiający eksploratora działań o zakresie DLPRuleMatch.](../media/dlp-activity-explorer.png)

Aby uzyskać więcej informacji, zobacz [Wprowadzenie do eksploratora działań](data-classification-activity-explorer.md)

Aby dowiedzieć się więcej o programie Microsoft Purview DLP, zobacz:

- [Dowiedz się więcej o ochronie przed utratą danych punktu końcowego](endpoint-dlp-learn-about.md)
- [Dowiedz się więcej o domyślnych zasadach ochrony przed utratą danych w usłudze Microsoft Teams (wersja zapoznawcza)](dlp-teams-default-policy.md)
- [Dowiedz się więcej na temat lokalnego skanera ochrony przed utratą danych](dlp-on-premises-scanner-learn.md)
- [Dowiedz się więcej o rozszerzeniu zgodności firmy Microsoft](dlp-chrome-learn-about.md)
- [Dowiedz się więcej o pulpicie nawigacyjnym alertów ochrony przed utratą danych](dlp-alerts-dashboard-learn.md)

Aby dowiedzieć się, jak używać ochrony przed utratą danych w celu zachowania zgodności z przepisami dotyczącymi prywatności danych, zobacz [Wdrażanie ochrony informacji dla przepisów dotyczących prywatności danych za pomocą usługi Microsoft Purview](../solutions/information-protection-deploy.md)  (aka.ms/m365dataprivacy).

## <a name="licensing-and-subscriptions"></a>Licencjonowanie i subskrypcje

Aby uzyskać szczegółowe informacje na temat subskrypcji obsługujących protokół DLP, zobacz [wymagania licencyjne dotyczące Information Protection](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).
