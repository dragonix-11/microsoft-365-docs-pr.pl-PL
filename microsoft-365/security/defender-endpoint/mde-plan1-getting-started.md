---
title: Wprowadzenie z Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1
description: Wprowadzenie usługi Defender dla punktu końcowego (plan 1). Dowiedz się, jak korzystać z Defender dla Chmury, zarządzać alertami i urządzeniami oraz wyświetlać raporty.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.date: 01/03/2022
ms.prod: m365-security
ms.technology: mdep1
ms.localizationpriority: medium
ms.reviewer: inbadian
f1.keywords: NOCSH
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.custom: intro-get-started
ms.openlocfilehash: c3e7f55a0dd8ad26f2b00b7e2d5840945e777a2a
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470334"
---
# <a name="get-started-with-microsoft-defender-for-endpoint-plan-1"></a>Wprowadzenie z Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Portal Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) umożliwia wyświetlanie informacji o wykrytych zagrożeniach, zarządzanie alertami i zdarzeniami, podjąć wszelkie wymagane działania dotyczące wykrytych zagrożeń oraz zarządzać urządzeniami. W Microsoft 365 Defender punktów końcowych 1 można rozpocząć interakcję z możliwościami ochrony przed zagrożeniami, które można uzyskać za pomocą usługi Defender for Endpoint Plan 1. W poniższych sekcjach opisano, jak rozpocząć pracę:

- [Portal Microsoft 365 Defender użytkowników](#the-microsoft-365-defender-portal)
- [Wyświetlanie alertów dotyczących zdarzeń i & zarządzanie nimi](#view-and-manage-incidents--alerts)
- [Zarządzanie urządzeniami](#manage-devices)
- [Wyświetlanie raportów](#view-reports)

## <a name="the-microsoft-365-defender-portal"></a>Portal Microsoft 365 Defender użytkowników

W portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) można wyświetlać alerty, zarządzać urządzeniami i wyświetlać raporty. Po zalogowaniu się do Microsoft 365 Defender strony głównej rozpoczniesz od strony głównej, jak pokazano na poniższej ilustracji:

:::image type="content" source="../../media/mde-p1/m365-defender-portal.png" alt-text="Portal Microsoft 365 Defender" lightbox="../../media/mde-p1/m365-defender-portal.png":::

Strona główna udostępnia zespołowi zabezpieczeń migawkowy widok zagregowany alertów, stanu urządzenia i wykrytych zagrożeń. Centrum Defender dla Chmury tak, aby zespół operacyjny ds. zabezpieczeń szybko i łatwo znalazł szukane informacje.

> [!NOTE]
> Nasze przykłady przedstawione w tym artykule mogą różnić się od tego, co widzisz w Twoim Microsoft 365 Defender portalu. To, co zobaczysz w portalu, zależy od licencji i uprawnień. Ponadto zespół zabezpieczeń może dostosować portal organizacji przez dodawanie, usuwanie i ponowne rozmieszczanie kart.

### <a name="cards-highlight-key-information-and-include-recommendations"></a>Karty wyróżniają najważniejsze informacje i zawierają zalecenia

Strona główna zawiera karty, takie jak karta Aktywne zdarzenia pokazana na poniższej ilustracji:

:::image type="content" source="../../media/mde-p1/active-incidents-card.png" alt-text="Karta Aktywne zdarzenia" lightbox="../../media/mde-p1/active-incidents-card.png":::

Karta zawiera szybki dostęp do informacji oraz link lub przycisk, który można wybrać w celu wyświetlenia bardziej szczegółowych informacji. Odwołując się do naszej przykładowej karty Aktywne zdarzenia, możemy wybrać  pozycję Wyświetl wszystkie zdarzenia, aby przejść do naszej listy zdarzeń.

:::image type="content" source="../../media/mde-p1/incidents.png" alt-text="Lista zdarzeń" lightbox="../../media/mde-p1/incidents.png":::

### <a name="navigation-bar-makes-it-easy-to-find-alerts-the-action-center-and-more"></a>Pasek nawigacyjny ułatwia znajdowanie alertów, Centrum akcji i nie tylko

Pasek nawigacyjny po lewej stronie ekranu umożliwia łatwe przechodzenie między zdarzeniami, alertami, Centrum akcji, raportami i ustawieniami. W poniższej tabeli opisano pasek nawigacyjny.<br/><br/>

| Element paska nawigacyjnego | Opis |
|:---|:---|
| **Strona główna** | Przechodzi do strony głównej w portalu [Microsoft 365 Defender sieci Web](../defender/microsoft-365-security-center-mde.md). |
| **Alerty o & zdarzeniach** | Rozszerza ten program, aby **wyświetlić alerty i zdarzenia****.** |
| **Alerty o & zdarzeniach** >  **Zdarzenia** | Przechodzenie do **listy Zdarzenia** . Zdarzenia są tworzone w przypadku wyzwolenia alertów i/lub wykrycia zagrożeń. Domyślnie na liście **Zdarzenia są** wyświetlane dane z ostatnich 30 dni, a jako pierwsze jest wymienione najnowsze zdarzenie. <br/><br/> Aby dowiedzieć się więcej, zobacz [Zdarzenia](view-incidents-queue.md). |
| **Alerty o & zdarzeniach** >  **Alerty** | Przechodzi do listy **Alerty** (nazywanej również kolejką **alertów**). Alerty są wyzwalane w przypadku wykrycia podejrzanych lub złośliwych plików, procesów lub zachowań. Domyślnie na liście **Alerty** są wyświetlane dane z ostatnich 30 dni, a jako pierwszy jest wymieniony najnowszy alert. <br/><br/> Aby dowiedzieć się więcej, zobacz [Alerty](alerts-queue.md). |
| **Centrum akcji** | Przechodzi do Centrum akcji, które umożliwia śledzenie działań naprawczych i akcji ręcznej odpowiedzi. Centrum akcji śledzi takie działania jak: <br/>— Program antywirusowy Microsoft Defender napotka złośliwy plik, a następnie blokuje/usuwa ten plik. <br/>— Zespół zabezpieczeń odizoluje urządzenie.<br/>- Program Defender for Endpoint wykrywa i podda plikowi kwarantannę. <br/><br/> Aby dowiedzieć się więcej, zobacz [Centrum akcji](auto-investigation-action-center.md). |
| **Wskaźnik bezpieczeństwa** | Wyświetla odzwierciedlenie stanu zabezpieczeń Organizacji oraz listę działań usprawnień i metryk. <br/><br/> Aby dowiedzieć się więcej, zobacz [Microsoft Secure Score](../defender/microsoft-secure-score.md). |
| **Edukacja centrum** | Przejdź do listy ścieżek nauki, do których możesz uzyskać dostęp, aby dowiedzieć się więcej o Microsoft 365 zabezpieczeń.  |
| **Punkty końcowe** >  **Wyszukiwanie** | Umożliwia przejście do strony, na której można wyszukać określone urządzenia według nazwy urządzenia. Na liście wyników można na pierwszy rzut oka zobaczyć szczegółowe informacje, takie jak poziom ryzyka i stan kondycji. |
|  **Punkty końcowe** >  **Spis urządzeń** | Przechodzi do listy urządzeń, które są podłączone do usługi Defender for Endpoint. Zapewnia informacje o urządzeniach, takich jak ich ekspozycja i poziomy ryzyka. <br/><br/> Aby dowiedzieć się więcej, zobacz [Spis urządzeń](machines-view-overview.md). |
|  **Punkty końcowe** >  **Ustawienia & bazowe** | Rozszerza, aby wyświetlić **informacje o planach bazowych zabezpieczeń** i **zarządzaniu konfiguracją**. |
|  **Punkty końcowe** >  **Ustawienia & bazowe** >  **Linie bazowe zabezpieczeń** | Linie bazowe zabezpieczeń to wstępnie skonfigurowane zasady i grupy ustawień, które mogą ułatwić wydajne i efektywne stosowanie zalecanych ustawień zabezpieczeń. Linie bazowe obejmują ustawienia oparte na najlepszych rozwiązaniach branżowych. Możesz zachować ustawienia domyślne lub dostosować swoje linie bazowe do potrzeb organizacji. <br/><br/> Aby dowiedzieć się więcej, zobacz [Konfigurowanie urządzeń](/mem/intune/protect/security-baselines) przenośnych z systemem Windows 10 w sieci Intune. |
|  **Punkty końcowe** >  **Ustawienia & bazowe** >  **Zarządzanie konfiguracją** | Przejdź do strony **Zarządzanie konfiguracją urządzeń** , na której możesz wyświetlić informacje o urządzeniach podłączonych do urządzenia i wykonać odpowiednie czynności, aby dodać więcej urządzeń. |
| **Raporty** | Umożliwia przejście do raportów, takich jak raport ochrony przed [zagrożeniami](threat-protection-reports.md)[, raport](machine-reports.md) kondycji urządzenia i zgodności oraz raport [ochrony sieci Web](web-protection-overview.md). |
| **Kondycja** | Zawiera **linki do centrum** Kondycja usługi **wiadomości**.  |
| **Kondycja** >  **Kondycja usługi** | Przechodzi do Kondycja usługi strony głównej w Centrum administracyjne platformy Microsoft 365. Ta strona umożliwia wyświetlenie stanu kondycji wszystkich usług dostępnych w ramach subskrypcji Twojej organizacji.   |
| **Kondycja** >  **Centrum wiadomości** | Przechodzi do Centrum wiadomości w Centrum administracyjne platformy Microsoft 365. Centrum wiadomości zawiera informacje o planowanych zmianach. W każdej wiadomości opisano nadchodzące zmiany, wpływ tej zmiany na użytkowników i sposób zarządzania zmianami. |  
| **Uprawnienia & ról** | Umożliwia udzielenie uprawnień do korzystania z portalu Microsoft 365 Defender internetowego. Uprawnienia są udzielane za pośrednictwem ról w usłudze Azure Active Directory (Azure AD). Wybierz rolę i zostanie wyświetlone okienko wysuwu. Wysuw zawiera link do usługi Azure AD, w którym można dodawać lub usuwać członków w grupie ról. <br/><br/> Aby dowiedzieć się więcej, zobacz [Zarządzanie dostępem do portalu za pomocą kontroli dostępu opartej na rolach](rbac.md).  |
| **Ustawienia** | Przechodzi do ustawień ogólnych twojego portalu Microsoft 365 Defender (wymienionych jako Centrum **zabezpieczeń) i** usługi Defender for Endpoint (wymienionych jako **Punkty końcowe**). <br/><br/> Aby dowiedzieć się więcej, zobacz [Ustawienia](../defender/microsoft-365-defender.md#the-microsoft-365-defender-portal). |
| **Więcej zasobów** | Wyświetla listę większej liczby portali i centrów, takich jak Azure Active Directory i Centrum zgodności platformy Microsoft 365. <br/><br/> Aby dowiedzieć się więcej, zobacz [Portale zabezpieczeń firmy Microsoft i centra administracyjne](../defender/portals.md). |

> [!TIP]
> Aby dowiedzieć się więcej, zobacz [omówienie Microsoft 365 Defender portalu internetowego](../defender/microsoft-365-security-center-mde.md).

## <a name="view-and-manage-incidents--alerts"></a>Wyświetlanie alertów dotyczących & i zarządzanie nimi

Po zalogowaniu się do portalu Microsoft 365 Defender pamiętaj o wyświetlaniu zdarzeń i alertach oraz zarządzaniu nimi. Zacznij od **listy Zdarzenia** . Na poniższej ilustracji przedstawiono listę zdarzeń, w tym jeden o wysokim poziomie ważności, a drugi o średniej ważności.

:::image type="content" source="../../media/mde-p1/incidents.png" alt-text="Lista zdarzeń":::

Wybierz zdarzenie, aby wyświetlić szczegółowe informacje o zdarzeniu. Szczegóły obejmują, jakie alerty zostały wyzwolone, ilu urządzeń i użytkowników wpłynęło na nie, i inne szczegóły. Na poniższej ilustracji przedstawiono przykładowe szczegóły zdarzenia.

:::image type="content" source="../../media/mde-p1/single-incident.png" alt-text="Szczegóły zdarzenia" lightbox="../../media/mde-p1/single-incident.png":::

Użyj kart **Alerty****, Urządzenia** i  Użytkownicy, aby wyświetlić więcej informacji, takich jak alerty, które zostały wyzwolone, urządzenia, których dotyczyło zdarzenie, i konta użytkowników, których dotyczy problem. W tym miejscu można podjąć działania ręczne, takie jak odizolowanie urządzenia, zatrzymanie i kwartyfowanie pliku itp.

> [!TIP]
> Aby dowiedzieć się więcej o **używaniu widoku Zdarzenia** , zobacz [Zarządzanie zdarzeniami](manage-incidents.md).

## <a name="manage-devices"></a>Zarządzanie urządzeniami

Aby wyświetlić urządzenia organizacji i zarządzać nimi, na pasku nawigacyjnym w obszarze **Punkty końcowe** wybierz pozycję **Spis urządzeń**. Zostanie wyświetlona lista urządzeń, jak pokazano na poniższej ilustracji:

:::image type="content" source="../../media/mde-p1/device-inventory.png" alt-text="Spis urządzeń" lightbox="../../media/mde-p1/device-inventory.png":::

Lista zawiera urządzenia, dla których zostały wygenerowane alerty. Domyślnie wyświetlane dane to ostatnie 30 dni, a najnowsze elementy są wyświetlane jako pierwsze. Wybierz urządzenie, aby wyświetlić więcej informacji na jego temat. Zostanie otwarte okienko wysuwu, jak pokazano na poniższej ilustracji:

:::image type="content" source="../../media/mde-p1/device-inventory-selecteddevice.png" alt-text="Wybrane szczegóły urządzenia" lightbox="../../media/mde-p1/device-inventory-selecteddevice.png":::

W okienku wysuwanym są wyświetlane szczegółowe informacje, takie jak aktywne alerty dotyczące urządzenia, oraz linki do działań, takich jak odizolowanie urządzenia.

Jeśli na urządzeniu są aktywne alerty, możesz je wyświetlić w okienku wysuwu. Wybierz pojedynczy alert, aby wyświetlić więcej szczegółów na jego temat. Możesz też podjąć działanie, takie jak Wyizoluj **urządzenie, aby** można było dokładniej zbadać urządzenie, minimalizując ryzyko zainfekowania innych urządzeń.

> [!TIP]
> Aby dowiedzieć się więcej, zobacz [Badanie urządzeń na liście Defender for Endpoint devices (Badanie urządzeń w programie Defender dla urządzeń końcowych](investigate-machines.md)).

## <a name="view-reports"></a>Wyświetlanie raportów

W programie Defender for Endpoint Plan 1 dostępnych jest kilka raportów w portalu usługi Microsoft 365 Defender sieci Web. Aby uzyskać dostęp do raportów, wykonaj następujące czynności:

1. Przejdź do Microsoft 365 Defender konta ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. Na pasku nawigacyjnym wybierz pozycję **Raporty**.

3. Wybierz raport z listy. Zobaczysz trzy następujące raporty:

   - Raport ochrony przed zagrożeniami
   - Raport kondycji urządzenia
   - Raport ochrony sieci Web

> [!TIP]
> Aby uzyskać więcej informacji, zobacz [Raporty o ochronie zagrożeń](threat-protection-reports.md).

### <a name="threat-protection-report"></a>Raport ochrony przed zagrożeniami

Aby uzyskać dostęp do raportu ochrony przed zagrożeniami, w portalu Microsoft 365 Defender **wybierz pozycję** Raporty, a następnie wybierz pozycję **Ochrona przed zagrożeniami**. Raport Ochrona przed zagrożeniami przedstawia trendy alertów, stan, kategorie i nie tylko. Widoki są rozmieszczone w dwóch kolumnach: **Trendy alertów** i **Stan alertu**, jak pokazano na poniższej ilustracji:

:::image type="content" source="../../media/mde-p1/threat-protection-report.png" alt-text="Raport ochrony przed zagrożeniami" lightbox="../../media/mde-p1/threat-protection-report.png":::

Przewiń w dół, aby wyświetlić wszystkie widoki na poszczególnych listach.

- Domyślnie w widokach w kolumnie Trendy  alertów są wyświetlane dane z ostatnich 30 dni, ale można ustawić wyświetlanie danych za ostatnie trzy miesiące, ostatnie sześć miesięcy lub niestandardowy zakres czasu (do 180 dni).
- Widoki w kolumnie **Stan alertu** są migawką z poprzedniego dnia biznesowego.

> [!TIP]
> Aby dowiedzieć się więcej, zobacz [Raport ochrony przed zagrożeniami w programie Defender dla punktu końcowego](threat-protection-reports.md).

### <a name="device-health-report"></a>Raport kondycji urządzenia

Aby uzyskać dostęp do raportu Kondycja urządzenia, w portalu Microsoft 365 Defender **wybierz pozycję** Raporty, a następnie wybierz **pozycję Kondycja urządzenia**. Raport Kondycja urządzenia zawiera informacje o stanie kondycji i programie antywirusowym na różnych urządzeniach w organizacji. Podobnie jak w [raporcie Ochrona](#threat-protection-report) przed zagrożeniami widoki są rozmieszczone w dwóch **kolumnach: Trendy** urządzeń i Podsumowanie **urządzeń, jak** pokazano na poniższej ilustracji:

:::image type="content" source="../../media/mde-p1/device-health-report.png" alt-text="Raport kondycji urządzenia" lightbox="../../media/mde-p1/device-health-report.png":::

Przewiń w dół, aby wyświetlić wszystkie widoki na poszczególnych listach. Domyślnie w widokach w kolumnie Trendy  urządzeń są wyświetlane dane z ostatnich 30 dni, ale możesz zmienić widok, aby wyświetlać dane za ostatnie trzy miesiące, ostatnie sześć miesięcy lub niestandardowy zakres czasu (do 180 dni). Widoki **podsumowania urządzenia** są migawkami z poprzedniego dnia biznesowego.

> [!TIP]
> Aby dowiedzieć się więcej, zobacz [Kondycja urządzenia](machine-reports.md).

### <a name="web-protection-report"></a>Raport ochrony sieci Web

Aby uzyskać dostęp do raportu Kondycja urządzenia, w portalu Microsoft 365 Defender **wybierz pozycję** Raporty, a następnie wybierz pozycję **Ochrona sieci Web**. Raport ochrony sieci Web pokazuje wykrywanie w czasie, takie jak złośliwe adresy URL i próby uzyskania dostępu do zablokowanych adresów URL, jak pokazano na poniższej ilustracji:

:::image type="content" source="../../media/mde-p1/web-protection-report.png" alt-text="Raport ochrony sieci Web" lightbox="../../media/mde-p1/web-protection-report.png":::

Przewiń w dół, aby wyświetlić wszystkie widoki w raporcie ochrony sieci Web. Niektóre widoki zawierają linki umożliwiające wyświetlenie szczegółowych informacji, skonfigurowanie funkcji ochrony przed zagrożeniami, a nawet zarządzanie wskaźnikami, które służą jako wyjątki w programie Defender dla punktu końcowego.

> [!TIP]
> Aby dowiedzieć się więcej, zobacz [Ochrona sieci Web](web-protection-overview.md).

## <a name="next-steps"></a>Następne kroki

- [Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](mde-p1-maintenance-operations.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender](microsoft-defender-endpoint.md)
