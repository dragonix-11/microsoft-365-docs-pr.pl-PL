---
title: Wprowadzenie z planem Ochrona punktu końcowego w usłudze Microsoft Defender 1
description: Wprowadzenie przy użyciu usługi Defender for Endpoint Plan 1. Dowiedz się, jak korzystać z Defender dla Chmury, zarządzać alertami i urządzeniami oraz wyświetlać raporty.
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
ms.openlocfilehash: d332cbf32f5423fb16abb158f9a30a18c2391a22
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64939350"
---
# <a name="get-started-with-microsoft-defender-for-endpoint-plan-1"></a>Wprowadzenie z planem Ochrona punktu końcowego w usłudze Microsoft Defender 1

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Portal Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) umożliwia wyświetlanie informacji o wykrytych zagrożeniach, zarządzanie alertami i zdarzeniami, wykonywanie wszelkich wymaganych działań w przypadku wykrytych zagrożeń i zarządzanie urządzeniami. W portalu Microsoft 365 Defender można rozpocząć interakcję z funkcjami ochrony przed zagrożeniami dostępnymi w usłudze Defender for Endpoint Plan 1. W poniższych sekcjach opisano sposób rozpoczęcia pracy:

- [Portal Microsoft 365 Defender](#the-microsoft-365-defender-portal)
- [Wyświetlanie zdarzeń & alertów i zarządzanie nimi](#view-and-manage-incidents--alerts)
- [Zarządzanie urządzeniami](#manage-devices)
- [Wyświetlanie raportów](#view-reports)

## <a name="the-microsoft-365-defender-portal"></a>Portal Microsoft 365 Defender

W portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) będziesz wyświetlać alerty, zarządzać urządzeniami i wyświetlać raporty. Po zalogowaniu się do portalu Microsoft 365 Defender zaczniesz od strony głównej, jak pokazano na poniższej ilustracji:

:::image type="content" source="../../media/mde-p1/m365-defender-portal.png" alt-text="Portal Microsoft 365 Defender" lightbox="../../media/mde-p1/m365-defender-portal.png":::

Strona główna udostępnia zespołowi ds. zabezpieczeń zagregowany widok migawek alertów, stanu urządzenia i wykrytych zagrożeń. Defender dla Chmury jest skonfigurowany tak, aby zespół ds. operacji zabezpieczeń mógł szybko i łatwo znaleźć informacje, których szuka.

> [!NOTE]
> Nasze przykłady przedstawione w tym artykule mogą różnić się od tego, co widzisz w portalu Microsoft 365 Defender. To, co widzisz w portalu, zależy od licencji i uprawnień. Ponadto zespół ds. zabezpieczeń może dostosować portal organizacji, dodając, usuwając i rozmieszczając karty.

### <a name="cards-highlight-key-information-and-include-recommendations"></a>Karty wyróżniają kluczowe informacje i zawierają zalecenia

Strona główna zawiera karty, takie jak karta Aktywne zdarzenia pokazana na poniższej ilustracji:

:::image type="content" source="../../media/mde-p1/active-incidents-card.png" alt-text="Karta Aktywne zdarzenia" lightbox="../../media/mde-p1/active-incidents-card.png":::

Karta udostępnia informacje na pierwszy rzut oka wraz z linkiem lub przyciskiem, który można wybrać, aby wyświetlić bardziej szczegółowe informacje. Odwołując się do przykładowej karty Aktywne zdarzenia, możemy wybrać pozycję **Wyświetl wszystkie zdarzenia** , aby przejść do naszej listy zdarzeń.

:::image type="content" source="../../media/mde-p1/incidents.png" alt-text="Lista zdarzeń" lightbox="../../media/mde-p1/incidents.png":::

### <a name="navigation-bar-makes-it-easy-to-find-alerts-the-action-center-and-more"></a>Pasek nawigacyjny ułatwia znajdowanie alertów, centrum akcji i nie tylko

Pasek nawigacyjny po lewej stronie ekranu umożliwia łatwe przechodzenie między zdarzeniami, alertami, centrum akcji, raportami i ustawieniami. W poniższej tabeli opisano pasek nawigacyjny.<br/><br/>

| Element paska nawigacyjnego | Opis |
|:---|:---|
| **Strona główna** | Przechodzi do strony głównej [portalu Microsoft 365 Defender](../defender/microsoft-365-security-center-mde.md). |
| **Zdarzenia & alerty** | Rozwija się, aby wyświetlić **zdarzenia** i **alerty**. |
| **Zdarzenia & alerty** >  **Incydentów** | Przechodzi do listy **Incydenty** . Zdarzenia są tworzone po wyzwoleniu alertów i/lub wykryciu zagrożeń. Domyślnie na liście **Zdarzenia** są wyświetlane dane z ostatnich 30 dni z najnowszym zdarzeniem wymienionym jako pierwsze. <br/><br/> Aby dowiedzieć się więcej, zobacz [Incydenty](view-incidents-queue.md). |
| **Zdarzenia & alerty** >  **Alerty** | Przechodzi do listy **Alerty** (nazywanej również **kolejką alertów**). Alerty są wyzwalane po wykryciu podejrzanego lub złośliwego pliku, procesu lub zachowania. Domyślnie na liście **Alerty** są wyświetlane dane z ostatnich 30 dni z najnowszym alertem wymienionym jako pierwszy. <br/><br/> Aby dowiedzieć się więcej, zobacz [Alerty](alerts-queue.md). |
| **Centrum akcji** | Przechodzi do centrum akcji, które śledzi akcje korygowania i ręcznego reagowania. Centrum akcji śledzi takie działania: <br/>— Program antywirusowy Microsoft Defender napotyka złośliwy plik, a następnie blokuje/usuwa ten plik. <br/>- Twój zespół ds. zabezpieczeń izoluje urządzenie.<br/>— Usługa Defender for Endpoint wykrywa plik i podda go kwarantannie. <br/><br/> Aby dowiedzieć się więcej, zobacz [Centrum akcji](auto-investigation-action-center.md). |
| **Wskaźnik bezpieczeństwa** | Przedstawia reprezentację stanu zabezpieczeń organizacji wraz z listą akcji poprawy i metryk. <br/><br/> Aby dowiedzieć się więcej, zobacz [Microsoft Secure Score (Wskaźnik bezpieczeństwa firmy Microsoft](../defender/microsoft-secure-score.md)). |
| **centrum Edukacja** | Przechodzi do listy ścieżek szkoleniowych, do których można uzyskać dostęp, aby dowiedzieć się więcej o Microsoft 365 możliwościach zabezpieczeń.  |
| **Punkty końcowe** >  **Szukaj** | Przechodzi do strony, na której można wyszukiwać określone urządzenia według nazwy urządzenia. Na liście wyników można szybko zobaczyć szczegóły, takie jak poziom ryzyka i stan kondycji. |
|  **Punkty końcowe** >  **Spis urządzeń** | Przechodzi do listy urządzeń dołączonych do usługi Defender for Endpoint. Zawiera informacje o urządzeniach, takie jak ich narażenie i poziom ryzyka. <br/><br/> Aby dowiedzieć się więcej, zobacz [Spis urządzeń](machines-view-overview.md). |
|  **Punkty końcowe** >  **Konfiguracja & punktów odniesienia** | Rozwija się, aby wyświetlić **punkty odniesienia zabezpieczeń** i **zarządzanie konfiguracją**. |
|  **Punkty końcowe** >  **Konfiguracja & planów bazowych** >  **Punkty odniesienia zabezpieczeń** | Punkty odniesienia zabezpieczeń to wstępnie skonfigurowane zasady i grupy ustawień, które mogą pomóc w wydajnym i skutecznym zastosowaniu zalecanych ustawień zabezpieczeń. Punkty odniesienia obejmują ustawienia oparte na najlepszych rozwiązaniach branżowych. Możesz zachować ustawienia domyślne lub dostosować punkty odniesienia zgodnie z potrzebami organizacji. <br/><br/> Aby dowiedzieć się więcej, zobacz [Konfigurowanie urządzeń Windows 10 w Intune przy użyciu punktów odniesienia zabezpieczeń](/mem/intune/protect/security-baselines). |
|  **Punkty końcowe** >  **Konfiguracja & planów bazowych** >  **Zarządzanie konfiguracją** | Przechodzi do strony **Zarządzanie konfiguracją urządzeń** , na której można wyświetlać informacje o dołączonych urządzeniach i wykonywać kroki w celu dołączenia większej liczby urządzeń. |
| **Raporty** | Przechodzi do raportów, takich jak [raport dotyczący ochrony przed zagrożeniami](threat-protection-reports.md), [raport kondycji i zgodności urządzenia](machine-reports.md) oraz [raport dotyczący ochrony sieci Web](web-protection-overview.md). |
| **Kondycja** | Zawiera linki do **Kondycja usługi** i **Centrum komunikatów**.  |
| **Zdrowia** >  **Kondycja usługi** | Przechodzi do strony Kondycja usługi w Centrum administracyjne platformy Microsoft 365. Ta strona umożliwia wyświetlanie stanu kondycji we wszystkich usługach dostępnych w ramach subskrypcji organizacji.   |
| **Zdrowia** >  **Centrum komunikatów** | Przechodzi do centrum komunikatów w Centrum administracyjne platformy Microsoft 365. Centrum komunikatów zawiera informacje o planowanych zmianach. Każdy komunikat zawiera opis nadchodzących zmian, wpływu na użytkowników i sposobu zarządzania zmianami. |  
| **Uprawnienia & ról** | Umożliwia udzielanie uprawnień do korzystania z portalu Microsoft 365 Defender. Uprawnienia są przyznawane za pośrednictwem ról w Azure Active Directory (Azure AD). Wybierz rolę i zostanie wyświetlone okienko wysuwane. Wysuwane okno zawiera link do usługi Azure AD, w którym można dodawać lub usuwać członków w grupie ról. <br/><br/> Aby dowiedzieć się więcej, zobacz [Zarządzanie dostępem do portalu przy użyciu kontroli dostępu opartej na rolach](rbac.md).  |
| **Ustawienia** | Przechodzi do ogólnych ustawień portalu Microsoft 365 Defender (wymienionego jako **Centrum zabezpieczeń**) i usługi Defender dla punktu końcowego (wymienionego jako **punkty końcowe**). <br/><br/> Aby dowiedzieć się więcej, zobacz [Ustawienia](../defender/microsoft-365-defender.md#the-microsoft-365-defender-portal). |
| **Więcej zasobów** | Wyświetla listę kolejnych portali i centrów, takich jak Azure Active Directory i portal zgodności usługi Microsoft Purview. <br/><br/> Aby dowiedzieć się więcej, zobacz [Portale zabezpieczeń firmy Microsoft i centra administracyjne](../defender/portals.md). |

> [!TIP]
> Aby dowiedzieć się więcej, zobacz [omówienie portalu Microsoft 365 Defender](../defender/microsoft-365-security-center-mde.md).

## <a name="view-and-manage-incidents--alerts"></a>Wyświetlanie zdarzeń & alertów i zarządzanie nimi

Po zalogowaniu się do portalu Microsoft 365 Defender upewnij się, że wyświetlasz zdarzenia i alerty oraz zarządzasz nimi. Zacznij od listy **zdarzeń** . Na poniższej ilustracji przedstawiono listę zdarzeń, w tym jeden o wysokiej ważności, a drugi o średniej ważności.

:::image type="content" source="../../media/mde-p1/incidents.png" alt-text="Lista zdarzeń":::

Wybierz zdarzenie, aby wyświetlić szczegóły dotyczące zdarzenia. Szczegółowe informacje obejmują alerty, które zostały wyzwolone, liczbę urządzeń i użytkowników, których dotyczy problem, oraz inne szczegóły. Na poniższej ilustracji przedstawiono przykład szczegółów zdarzenia.

:::image type="content" source="../../media/mde-p1/single-incident.png" alt-text="Szczegóły zdarzenia" lightbox="../../media/mde-p1/single-incident.png":::

Użyj kart **Alerty**, **Urządzenia** i **Użytkownicy** , aby wyświetlić więcej informacji, takich jak alerty, które zostały wyzwolone, urządzenia, których dotyczy problem, i konta użytkowników, których dotyczy problem. Z tego miejsca można wykonywać ręczne akcje reagowania, takie jak izolowanie urządzenia, zatrzymywanie i kwazarowanie pliku itd.

> [!TIP]
> Aby dowiedzieć się więcej na temat korzystania z widoku **Zdarzenia** , zobacz [Zarządzanie zdarzeniami](manage-incidents.md).

## <a name="manage-devices"></a>Zarządzanie urządzeniami

Aby wyświetlić urządzenia organizacji i zarządzać nimi, na pasku **nawigacyjnym w obszarze Punkty końcowe** wybierz pozycję **Spis urządzeń**. Zostanie wyświetlona lista urządzeń, jak pokazano na poniższej ilustracji:

:::image type="content" source="../../media/mde-p1/device-inventory.png" alt-text="Spisz urządzeń" lightbox="../../media/mde-p1/device-inventory.png":::

Lista zawiera urządzenia, dla których zostały wygenerowane alerty. Domyślnie wyświetlane dane są używane w ciągu ostatnich 30 dni z najnowszymi elementami wymienionymi jako pierwsze. Wybierz urządzenie, aby wyświetlić więcej informacji na jego temat. Zostanie otwarte okienko wysuwane, jak pokazano na poniższej ilustracji:

:::image type="content" source="../../media/mde-p1/device-inventory-selecteddevice.png" alt-text="Szczegóły wybranego urządzenia" lightbox="../../media/mde-p1/device-inventory-selecteddevice.png":::

Okienko wysuwane wyświetla szczegóły, takie jak wszystkie aktywne alerty dla urządzenia, i zawiera linki do podjęcia akcji, takie jak izolowanie urządzenia.

Jeśli na urządzeniu są aktywne alerty, możesz je wyświetlić w okienku wysuwanym. Wybierz pojedynczy alert, aby wyświetlić więcej szczegółów na jego temat. Możesz też wykonać akcję, taką jak **Izolowanie urządzenia**, aby można było dokładniej zbadać urządzenie, minimalizując ryzyko zainfekowania innych urządzeń.

> [!TIP]
> Aby dowiedzieć się więcej, zobacz [Badanie urządzeń na liście urządzeń usługi Defender for Endpoint](investigate-machines.md).

## <a name="view-reports"></a>Wyświetlanie raportów

W usłudze Defender for Endpoint Plan 1 w portalu Microsoft 365 Defender dostępnych jest kilka raportów. Aby uzyskać dostęp do raportów, wykonaj następujące kroki:

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. Na pasku nawigacyjnym wybierz pozycję **Raporty**.

3. Wybierz raport z listy. Zostaną wyświetlone następujące trzy raporty:

   - Raport ochrony przed zagrożeniami
   - Raport kondycji urządzenia
   - Raport dotyczący ochrony sieci Web

> [!TIP]
> Aby uzyskać więcej informacji, zobacz [Raporty dotyczące ochrony przed zagrożeniami](threat-protection-reports.md).

### <a name="threat-protection-report"></a>Raport ochrony przed zagrożeniami

Aby uzyskać dostęp do raportu ochrony przed zagrożeniami, w portalu Microsoft 365 Defender wybierz pozycję **Raporty**, a następnie wybierz pozycję **Ochrona przed zagrożeniami**. Raport Threat Protection przedstawia trendy alertów, stan, kategorie i nie tylko. Widoki są rozmieszczone w dwóch kolumnach: **Trendy alertów** i **Stan alertu**, jak pokazano na poniższej ilustracji:

:::image type="content" source="../../media/mde-p1/threat-protection-report.png" alt-text="Raport ochrony przed zagrożeniami" lightbox="../../media/mde-p1/threat-protection-report.png":::

Przewiń w dół, aby wyświetlić wszystkie widoki na każdej liście.

- Domyślnie widoki w kolumnie **Trendy alertów** wyświetlają dane z ostatnich 30 dni, ale można ustawić widok do wyświetlania danych z ostatnich trzech miesięcy, ostatnich sześciu miesięcy lub niestandardowego zakresu czasu (do 180 dni).
- Widoki w kolumnie **Stan alertu** są migawką z poprzedniego dnia roboczego.

> [!TIP]
> Aby dowiedzieć się więcej, zobacz [Raport ochrony przed zagrożeniami w usłudze Defender for Endpoint](threat-protection-reports.md).

### <a name="device-health-report"></a>Raport kondycji urządzenia

Aby uzyskać dostęp do raportu kondycji urządzenia, w portalu Microsoft 365 Defender wybierz pozycję **Raporty**, a następnie wybierz pozycję **Kondycja urządzenia**. Raport Kondycja urządzenia pokazuje stan kondycji i oprogramowanie antywirusowe na różnych urządzeniach w organizacji. Podobnie jak w [raporcie Ochrona przed zagrożeniami](#threat-protection-report) widoki są rozmieszczone w dwóch kolumnach: **Trendy urządzeń** i **Podsumowanie urządzenia**, jak pokazano na poniższej ilustracji:

:::image type="content" source="../../media/mde-p1/device-health-report.png" alt-text="Raport kondycji urządzenia" lightbox="../../media/mde-p1/device-health-report.png":::

Przewiń w dół, aby wyświetlić wszystkie widoki na każdej liście. Domyślnie widoki w kolumnie **Trendy urządzeń** wyświetlają dane z ostatnich 30 dni, ale można zmienić widok, aby wyświetlić dane z ostatnich trzech miesięcy, ostatnich sześciu miesięcy lub niestandardowego zakresu czasu (do 180 dni). Widoki **podsumowania urządzenia** to migawki z poprzedniego dnia roboczego.

> [!TIP]
> Aby dowiedzieć się więcej, zobacz [Kondycja urządzenia](machine-reports.md).

### <a name="web-protection-report"></a>Raport dotyczący ochrony sieci Web

Aby uzyskać dostęp do raportu kondycji urządzenia, w portalu Microsoft 365 Defender wybierz pozycję **Raporty**, a następnie wybierz pozycję **Ochrona w Internecie**. Raport dotyczący ochrony sieci Web pokazuje wykrycia w czasie, takie jak złośliwe adresy URL i próby uzyskania dostępu do zablokowanych adresów URL, jak pokazano na poniższej ilustracji:

:::image type="content" source="../../media/mde-p1/web-protection-report.png" alt-text="Raport dotyczący ochrony sieci Web" lightbox="../../media/mde-p1/web-protection-report.png":::

Przewiń w dół, aby wyświetlić wszystkie widoki w raporcie ochrony sieci Web. Niektóre widoki zawierają linki, które umożliwiają wyświetlanie dodatkowych szczegółów, konfigurowanie funkcji ochrony przed zagrożeniami, a nawet zarządzanie wskaźnikami, które służą jako wyjątki w usłudze Defender for Endpoint.

> [!TIP]
> Aby dowiedzieć się więcej, zobacz [Ochrona w internecie](web-protection-overview.md).

## <a name="next-steps"></a>Następne kroki

- [Zarządzanie planem Ochrona punktu końcowego w usłudze Microsoft Defender 1](mde-p1-maintenance-operations.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender](microsoft-defender-endpoint.md)
