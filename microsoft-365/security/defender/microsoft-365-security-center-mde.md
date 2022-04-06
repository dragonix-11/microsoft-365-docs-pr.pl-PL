---
title: Ochrona punktu końcowego w usłudze Microsoft Defender w Microsoft 365 Defender
description: Dowiedz się więcej o zmianach z Centrum zabezpieczeń usługi Microsoft Defender na Microsoft 365 Defender
keywords: Wprowadzenie do Microsoft 365 Defender, Ochrona usługi Office 365 w usłudze Microsoft Defender, Ochrona punktu końcowego w usłudze Microsoft Defender, MDO, MDE, portalu zabezpieczeń, usługi Defender portal zabezpieczeń
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: 04/21/2021
audience: ITPro
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.openlocfilehash: bac70dd864e1ab72fae5fbefa2a8da12cce4f6e7
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64667235"
---
# <a name="microsoft-defender-for-endpoint-in-microsoft-365-defender"></a>Ochrona punktu końcowego w usłudze Microsoft Defender w Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="quick-reference"></a>Szybkie odwołanie

Obraz i poniższa tabela zawierają listę zmian w nawigacji między Centrum zabezpieczeń usługi Microsoft Defender i Microsoft 365 Defender.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/mde-m3d-security-center.png" alt-text="Nowe lokalizacje w portalu Microsoft 365 Defender" lightbox="../../media/mde-m3d-security-center.png":::

| Centrum zabezpieczeń usługi Microsoft Defender | Microsoft 365 Defender |
|---------|---------|
| Pulpity nawigacyjne <ul><li>Operacje zabezpieczeń</li><li>Analiza zagrożeń</li></ul>  |Home <ul><li>Analiza zagrożeń</li></ul>   |
| Zdarzenia | Zdarzenia & alerty |
| Spisz urządzeń | Spisz urządzeń |
| Kolejka alertów | Zdarzenia & alerty |
| Zautomatyzowane badania | Centrum akcji |
| Zaawansowane wyszukiwanie zagrożeń | Polowanie |
| Raporty | Raporty |
| Interfejsy API & partnerów | Interfejsy API & partnerów |
| Zarządzanie lukami w zabezpieczeniach & zagrożeń | Zarządzanie lukami w zabezpieczeniach |
| Ewaluacje i samouczki | Samouczki dotyczące & oceny |
| Zarządzanie konfiguracją | Zarządzanie konfiguracją |
| Ustawienia | Ustawienia | 

Ulepszona [Microsoft 365 Defender](microsoft-365-defender.md#the-microsoft-365-defender-portal) w usłudze <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a> łączy funkcje zabezpieczeń, które chronią, wykrywają, badają i reagują na zagrożenia związane z pocztą e-mail, współpracą, tożsamością i urządzeniami. Łączy to funkcje z istniejących portali zabezpieczeń firmy Microsoft, w tym Centrum zabezpieczeń usługi Microsoft Defender i centrum Office 365 Security & Compliance.

Jeśli znasz Centrum zabezpieczeń usługi Microsoft Defender, ten artykuł ułatwia opisanie niektórych zmian i ulepszeń w Microsoft 365 Defender. Istnieją jednak pewne nowe i zaktualizowane elementy, o których należy pamiętać.

Historycznie [Centrum zabezpieczeń usługi Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/portal-overview) był domem dla Ochrona punktu końcowego w usłudze Microsoft Defender. Enterprise zespoły ds. zabezpieczeń używały go do monitorowania i reagowania na alerty o potencjalnych zaawansowanych trwałych działaniach związanych z zagrożeniami lub naruszeniach danych. Aby zmniejszyć liczbę portali, Microsoft 365 Defender będzie miejscem do monitorowania zabezpieczeń i zarządzania nimi w tożsamościach, danych, urządzeniach, aplikacjach i infrastrukturze firmy Microsoft.

Ochrona punktu końcowego w usłudze Microsoft Defender w Microsoft 365 Defender obsługuje [udzielanie dostępu do zarządzanych dostawców usług zabezpieczeń w](/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access) taki sam sposób, [jak w przypadku Centrum zabezpieczeń usługi Microsoft Defender](mssp-access.md).

> [!IMPORTANT]
> To, co widzisz w Microsoft 365 Defender, zależy od bieżących subskrypcji. Jeśli na przykład nie masz licencji na Ochrona usługi Office 365 w usłudze Microsoft Defender, sekcja Współpraca & poczty e-mail nie zostanie wyświetlona.

> [!Note]
> Microsoft 365 Defender jest niedostępna dla:
>- us Government Community Cloud (GCC)
>- Us Government Community Cloud High (GCC High)
>- Departament Obrony USA
>- Wszystkie instytucje rządowe USA z licencjami komercyjnymi

Przyjrzyj się Microsoft 365 Defender pod adresem <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a>.

Dowiedz się więcej o korzyściach: [omówienie Microsoft 365 Defender](microsoft-365-defender.md)

## <a name="whats-changed"></a>Co się zmieniło

Ta tabela zawiera krótkie odwołanie do zmian między Centrum zabezpieczeń usługi Microsoft Defender a Microsoft 365 Defender.

### <a name="alerts-and-actions"></a>Alerty i akcje

| Obszar | Opis zmiany |
|---------|---------|
| [Zdarzenia & alerty](incidents-overview.md)  | W Microsoft 365 Defender można zarządzać zdarzeniami i alertami we wszystkich punktach końcowych, wiadomościach e-mail i tożsamościach. Zbiegają się środowiska, aby ułatwić znajdowanie powiązanych zdarzeń. Aby uzyskać więcej informacji, zobacz [Omówienie zdarzeń](incidents-overview.md).   |
| [Polowanie](advanced-hunting-overview.md)  |  Modyfikowanie niestandardowych reguł wykrywania utworzonych w Ochrona punktu końcowego w usłudze Microsoft Defender w celu uwzględnienia tabel tożsamości i wiadomości e-mail automatycznie przenosi je do Microsoft 365 Defender. Odpowiednie alerty będą również wyświetlane w Microsoft 365 Defender. Aby uzyskać więcej informacji na temat tych zmian, przeczytaj [Migrowanie niestandardowych reguł wykrywania](advanced-hunting-migrate-from-mde.md#migrate-custom-detection-rules). <br><br>Tabela `DeviceAlertEvents` zaawansowanego wyszukiwania zagrożeń nie jest dostępna w Microsoft 365 Defender. Aby wysyłać zapytania dotyczące informacji o alertach specyficznych dla urządzenia w Microsoft 365 Defender, możesz użyć `AlertInfo` tabel i`AlertEvidence`, aby uwzględnić jeszcze więcej informacji z różnych źródeł. Utwórz następne zapytanie związane z urządzeniem, wykonując czynności opisane w [temacie Write querys without DeviceAlertEvents (Pisanie zapytań bez funkcji DeviceAlertEvents](advanced-hunting-migrate-from-mde.md#write-queries-without-devicealertevents)).|
|[Centrum akcji](m365d-action-center.md)    | Wyświetla listę oczekujących i zakończonych akcji, które zostały wykonane po zautomatyzowanych badaniach i akcjach korygowania. Wcześniej centrum akcji w Centrum zabezpieczeń usługi Microsoft Defender wyświetlało oczekujące i ukończone akcje dotyczące działań korygowania wykonywanych tylko na urządzeniach, podczas gdy zautomatyzowane badania wyświetlały alerty i stan. W ulepszonej Microsoft 365 Defender centrum akcji łączy akcje korygowania i badania dotyczące poczty e-mail, urządzeń i użytkowników — wszystko to w jednej lokalizacji.  |
| [Analiza zagrożeń](threat-analytics.md) |  Przesuń na górę paska nawigacyjnego, aby ułatwić odnajdywanie i używanie. Teraz zawiera informacje o zagrożeniach zarówno dla punktów końcowych, jak i poczty e-mail i współpracy.    |

### <a name="endpoints"></a>Punkty końcowe

| Obszar | Opis zmiany |
|---------|---------|
|Szukaj   |  Pasek wyszukiwania znajduje się w górnej części strony. Sugestie są udostępniane podczas wpisywania. W usłudze Defender for Endpoint i Defender for Identity można wyszukiwać następujące jednostki: <br><br> - **Urządzenia** — obsługiwane zarówno w usłudze Defender for Endpoint, jak i w usłudze Defender for Identity. Można nawet użyć operatorów wyszukiwania, na przykład można użyć "contains" do wyszukiwania części nazwy hosta. <br><br> - **Użytkownicy** — obsługiwane zarówno w przypadku usługi Defender for Endpoint, jak i usługi Defender for Identity. <br><br> - **Pliki, adresy IP i adresy URL** — takie same możliwości jak w usłudze Defender for Endpoint. <br> UWAGA: *Wyszukiwania adresów IP i adresów URL są dokładnie zgodne i nie są wyświetlane na stronie wyników wyszukiwania — prowadzą bezpośrednio do strony jednostki.  <br><br> - **TVM** — takie same możliwości jak w usłudze Defender for Endpoint (luki w zabezpieczeniach, oprogramowanie i zalecenia). <br><br>  Strona rozszerzonych wyników wyszukiwania scentralizuje wyniki ze wszystkich jednostek.  |
|[Pulpit nawigacyjny](/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard)   |  To jest pulpit nawigacyjny operacji zabezpieczeń. Zapoznaj się z omówieniem liczby aktywnych alertów, które urządzenia są zagrożone, którzy użytkownicy są zagrożeni, oraz poziomu ważności alertów, urządzeń i użytkowników. Możesz również sprawdzić, czy jakiekolwiek urządzenia mają problemy z czujnikami, ogólną kondycję usługi i jak wykryto wszystkie nierozwiązane alerty. |
|Spisz urządzeń | Brak zmian. |
|[Zarządzanie lukami w zabezpieczeniach](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)    |    Nazwa została skrócona, aby zmieścić się w okienku nawigacji. Jest taka sama jak sekcja Zarządzanie zagrożeniami i lukami ze wszystkimi stronami poniżej.     |
| Partnerzy i interfejsy API | Brak zmian. |
| Samouczki dotyczące ocen &    |     Nowe możliwości testowania i uczenia się.     |
| Zarządzanie konfiguracją   |  Brak zmian.  |

> [!NOTE]
> **Automatyczne badanie i korygowanie** jest teraz częścią zdarzeń. Zdarzenia zautomatyzowanego badania i korygowania można wyświetlić na karcie **Badanie > zdarzenia** .

> [!TIP]
> Wyszukiwanie urządzeń odbywa się z punktów końcowych > wyszukiwania.

### <a name="access-and-reporting"></a>Dostęp i raportowanie

| Obszar | Opis zmiany |
|---------|---------|
| Raporty  | Zobacz raporty dotyczące punktów końcowych i współpracy & poczty e-mail, w tym ochrony przed zagrożeniami, kondycji i zgodności urządzeń oraz urządzeń narażonych na zagrożenia. |
| Kondycja  |  Obecnie łączy się ze stroną "Kondycja usługi" w [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com/). |
| Ustawienia |  Zarządzaj ustawieniami Microsoft 365 Defender, punktów końcowych, współpracy & poczty e-mail, tożsamości i odnajdywania urządzeń.   |

## <a name="microsoft-365-security-navigation-and-capabilities"></a>Microsoft 365 nawigacji i możliwości zabezpieczeń

Nawigacja po lewej stronie lub pasek szybkiego uruchamiania będą wyglądać znajomo. Istnieją jednak pewne nowe i zaktualizowane elementy w portalu Microsoft 365 Defender. 

### <a name="incidents-and-alerts"></a>Zdarzenia i alerty

Łączy zarządzanie zdarzeniami i alertami w wiadomościach e-mail, urządzeniach i tożsamościach. Strona alertu zawiera pełny kontekst alertu przez połączenie sygnałów ataku w celu utworzenia szczegółowego scenariusza. Nowe, ujednolicone środowisko łączy teraz spójny widok alertów w obciążeniach. Możesz szybko klasyfikować, badać i podejmować skuteczne działania.

- [Dowiedz się więcej o zdarzeniach](incidents-overview.md)
- [Dowiedz się więcej o zarządzaniu alertami](investigate-alerts.md)

:::image type="content" source="../../media/converge-1-alerts-and-actions.png" alt-text="Pasek szybkiego uruchamiania Alerty i akcje w portalu Microsoft 365 Defender" lightbox="../../media/converge-1-alerts-and-actions.png":::

### <a name="hunting"></a>Polowanie

Proaktywne wyszukiwanie zagrożeń, złośliwego oprogramowania i złośliwych działań w punktach końcowych, Office 365 skrzynkach pocztowych i nie tylko przy użyciu [zaawansowanych zapytań wyszukiwania zagrożeń](advanced-hunting-overview.md). Te zaawansowane zapytania mogą służyć do lokalizowania i przeglądania wskaźników zagrożeń i jednostek dla znanych i potencjalnych zagrożeń.

[Niestandardowe reguły wykrywania](custom-detection-rules.md) można tworzyć na podstawie zaawansowanych zapytań wyszukiwania zagrożeń, aby ułatwić aktywne obserwowanie zdarzeń, które mogą wskazywać na działanie naruszenia zabezpieczeń i nieprawidłowo skonfigurowane urządzenia.


### <a name="action-center"></a>Centrum akcji

Centrum akcji przedstawia badania utworzone za pomocą funkcji zautomatyzowanego badania i reagowania. Ta zautomatyzowana funkcja samonaprawiania w Microsoft 365 Defender może pomóc zespołom ds. zabezpieczeń, automatycznie reagując na określone zdarzenia.

[Dowiedz się więcej o Centrum akcji](m365d-action-center.md).

### <a name="threat-analytics"></a>Analiza zagrożeń

Uzyskaj analizę zagrożeń od ekspertów badaczy zabezpieczeń firmy Microsoft. Usługa Threat Analytics pomaga zespołom ds. zabezpieczeń być wydajniejszym w obliczu pojawiających się zagrożeń. Analiza zagrożeń obejmuje:

- Wykrywanie i środki zaradcze związane z pocztą e-mail z Ochrona usługi Office 365 w usłudze Microsoft Defender. Jest to dodatek do danych punktu końcowego już dostępnych z Ochrona punktu końcowego w usłudze Microsoft Defender.
- Widok zdarzeń związany z zagrożeniami.
- Ulepszone środowisko umożliwiające szybkie identyfikowanie i używanie praktycznych informacji w raportach.

Dostęp do analizy zagrożeń można uzyskać z lewego górnego paska nawigacyjnego w Microsoft 365 Defender lub z dedykowanej karty pulpitu nawigacyjnego, która pokazuje najważniejsze zagrożenia dla organizacji.

Dowiedz się więcej o [sposobie śledzenia pojawiających się zagrożeń i reagowania na nie za pomocą analizy zagrożeń](./threat-analytics.md).

### <a name="endpoints-section"></a>Sekcja Punkty końcowe

Wyświetlanie zabezpieczeń punktów końcowych w organizacji i zarządzanie nimi. Jeśli użyto Centrum zabezpieczeń usługi Microsoft Defender, będzie to wyglądać znajomo.

:::image type="content" source="../../media/converge-2-endpoints.png" alt-text="Pasek szybkiego uruchamiania punktów końcowych w portalu Microsoft 365 Defender" lightbox="../../media/converge-2-endpoints.png":::

### <a name="access-and-reports"></a>Dostęp i raporty

Wyświetlanie raportów, zmienianie ustawień i modyfikowanie ról użytkowników.

:::image type="content" source="../../media/converge-4-access-and-reporting-new.png" alt-text="Pasek szybkiego uruchamiania dostępu i raportowania w portalu Microsoft 365 Defender" lightbox="../../media/converge-4-access-and-reporting-new.png":::

### <a name="siem-api-connections"></a>Połączenia interfejsu API SIEM

Jeśli używasz [interfejsu API SIEM usługi Defender for Endpoint](../defender-endpoint/enable-siem-integration.md), możesz nadal to robić. Dodaliśmy nowe linki do ładunku interfejsu API, które wskazują stronę alertu lub stronę zdarzenia w portalu zabezpieczeń Microsoft 365. Nowe pola interfejsu API obejmują pola LinkToMTP i IncidentLinkToMTP. Aby uzyskać więcej informacji, zobacz [Przekierowywanie kont z Ochrona punktu końcowego w usłudze Microsoft Defender do Microsoft 365 Defender](./microsoft-365-security-mde-redirection.md).

### <a name="email-alerts"></a>Alerty poczty e-mail

Możesz nadal używać alertów poczty e-mail dla usługi Defender dla punktu końcowego. Dodaliśmy nowe linki w wiadomościach e-mail, które wskazują stronę alertu lub stronę zdarzenia w Microsoft 365 Defender. Aby uzyskać więcej informacji, zobacz [Przekierowywanie kont z Ochrona punktu końcowego w usłudze Microsoft Defender do Microsoft 365 Defender](./microsoft-365-security-mde-redirection.md).

### <a name="managed-security-service-providers-mssp"></a>Dostawcy usług zabezpieczeń zarządzanych (MSSP)

Logowanie się do wielu dzierżaw jednocześnie w tej samej sesji przeglądania nie jest obecnie obsługiwane w ujednoliconym portalu. Możesz zrezygnować z automatycznego przekierowania, [wracając do poprzedniego portalu Ochrona punktu końcowego w usłudze Microsoft Defender](microsoft-365-security-mde-redirection.md#can-i-go-back-to-using-the-former-portal), aby zachować tę funkcję do czasu rozwiązania problemu.

## <a name="related-information"></a>Informacje pokrewne

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender w Microsoft 365 Defender](microsoft-365-security-center-mde.md)
- [Przekierowywanie kont z Ochrona punktu końcowego w usłudze Microsoft Defender do Microsoft 365 Defender](microsoft-365-security-mde-redirection.md)
