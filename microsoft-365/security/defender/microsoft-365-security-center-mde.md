---
title: Ochrona punktu końcowego w usłudze Microsoft Defender w programie Microsoft 365 Defender
description: Informacje o zmianach w Centrum zabezpieczeń usługi Microsoft Defender do Microsoft 365 Defender
keywords: Wprowadzenie do aplikacji Microsoft 365 Defender, Ochrona usługi Office 365 w usłudze Microsoft Defender, Ochrona punktu końcowego w usłudze Microsoft Defender, MDO, MDE, portalu zabezpieczeń, usługi Defender portal zabezpieczeń
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
ms.openlocfilehash: fa9833572a57e0ea81978f25a7d8d34db068109a
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2022
ms.locfileid: "64501118"
---
# <a name="microsoft-defender-for-endpoint-in-microsoft-365-defender"></a>Ochrona punktu końcowego w usłudze Microsoft Defender w programie Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="quick-reference"></a>Podręczny przewodnik

Na obrazie i w poniższej tabeli przedstawiono zmiany w nawigacji między Centrum zabezpieczeń usługi Microsoft Defender i Microsoft 365 Defender.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/mde-m3d-security-center.png" alt-text="Nowe lokalizacje w portalu Microsoft 365 Defender sieci Microsoft 365 Defender." lightbox="../../media/mde-m3d-security-center.png":::

| Centrum zabezpieczeń usługi Microsoft Defender | Microsoft 365 Defender |
|---------|---------|
| Pulpity nawigacyjne <ul><li>Operacje zabezpieczeń</li><li>Analiza zagrożeń</li></ul>  |Home <ul><li>Analiza zagrożeń</li></ul>   |
| Zdarzenia | Alerty o & zdarzeniach |
| Spis urządzeń | Spis urządzeń |
| Kolejka alertów | Alerty o & zdarzeniach |
| Zautomatyzowane badania | Centrum akcji |
| Zaawansowane wyszukiwanie zagrożeń | Goniące |
| Raporty | Raporty |
| Interfejsy API & partnerów | Interfejsy API & partnerów |
| Zarządzanie & zagrożeniami | Zarządzanie lukami w zabezpieczeniach |
| Oceny i samouczki | Samouczki & oceny |
| Zarządzanie konfiguracją | Zarządzanie konfiguracją |
| Ustawienia | Ustawienia | 

Ulepszona [Microsoft 365 Defender](microsoft-365-defender.md#the-microsoft-365-defender-portal) łączy <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a> funkcje zabezpieczeń, które chronią, wykrywają, analizują i reagują na wiadomości e-mail, współpracę, tożsamość i zagrożenia dla urządzeń. W ten sposób dostępne są funkcje istniejących portali zabezpieczeń firmy Microsoft, w tym Centrum zabezpieczeń usługi Microsoft Defender zabezpieczeń firmy Microsoft oraz centrum Office 365 zabezpieczeń & zgodności.

Jeśli znasz tę Centrum zabezpieczeń usługi Microsoft Defender, ten artykuł zawiera opis niektórych zmian i ulepszeń w Microsoft 365 Defender. Istnieje jednak kilka nowych i zaktualizowanych elementów, o których warto pamiętać.

W przeszłości ten [Centrum zabezpieczeń usługi Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/portal-overview) był domem dla Ochrona punktu końcowego w usłudze Microsoft Defender. Enterprise zabezpieczeń używali jej do monitorowania i odpowiadania na alerty o potencjalnych zaawansowanych trwałych działaniach zagrożeń lub naruszeniach danych. Aby zmniejszyć liczbę portali, witryna Microsoft 365 Defender będzie domem monitorowania zabezpieczeń tożsamości firmy Microsoft, danych, urządzeń, aplikacji i infrastruktury oraz zarządzania nimi.

Ochrona punktu końcowego w usłudze Microsoft Defender w programie Microsoft 365 Defender obsługuje udzielanie dostępu do zarządzanych dostawców usług zabezpieczeń [w](/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access) taki sam sposób, jak dostęp jest [udzielany w Centrum zabezpieczeń usługi Microsoft Defender](mssp-access.md).

> [!IMPORTANT]
> To, co widzisz w Microsoft 365 Defender, zależy od aktualnych subskrypcji. Jeśli na przykład nie masz licencji na usługę Ochrona usługi Office 365 w usłudze Microsoft Defender, sekcja Współpraca z innymi & e-mail nie będzie wyświetlana.

> [!Note]
> Microsoft 365 Defender jest niedostępne dla:
>- Us Government Community Cloud (GCC)
>- Us Government Community Cloud High (GCC High)
>- Departament Obrony Stanów Zjednoczonych
>- Wszystkie instytucje rządowe Stanów Zjednoczonych z licencjami komercyjnymi

Zobacz Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a>.

Dowiedz się więcej o zaletach: [Omówienie funkcji Microsoft 365 Defender](microsoft-365-defender.md)

## <a name="whats-changed"></a>Co się zmieniło

Ta tabela zawiera krótkie odwołanie do zmian między Centrum zabezpieczeń usługi Microsoft Defender i Microsoft 365 Defender.

### <a name="alerts-and-actions"></a>Alerty i akcje

| Obszar | Opis zmiany |
|---------|---------|
| [Alerty o & zdarzeniach](incidents-overview.md)  | W Microsoft 365 Defender możesz zarządzać zdarzeniami i alertami we wszystkich punktach końcowych, wiadomościach e-mail i tożsamościach. Zbiegaliśmy się z tym, co pomaga łatwiej znaleźć powiązane zdarzenia. Aby uzyskać więcej informacji, zobacz [Omówienie zdarzeń](incidents-overview.md).   |
| [Goniące](advanced-hunting-overview.md)  |  Modyfikowanie niestandardowych reguł wykrywania utworzonych w Ochrona punktu końcowego w usłudze Microsoft Defender w celu dołączyć tabele tożsamości i poczty e-mail automatycznie przenosi je do Microsoft 365 Defender. Odpowiadające im alerty będą również wyświetlane w Microsoft 365 Defender. Aby uzyskać więcej szczegółowych informacji na temat tych zmian, zobacz [Migrowanie niestandardowych reguł wykrywania](advanced-hunting-migrate-from-mde.md#migrate-custom-detection-rules). <br><br>W `DeviceAlertEvents` programie nie jest dostępna tabela do zaawansowanego wyszukiwania Microsoft 365 Defender. Do wykonywania zapytań dotyczących alertów dotyczących określonych urządzeń w Microsoft 365 Defender można `AlertInfo` `AlertEvidence` używać tabel i tabel w celu uwzględnienia jeszcze większej liczby informacji ze zróżnicowanego zestawu źródeł. Stwórz następne zapytanie związane z urządzeniem, korzystając z [zapytań zapisu bez DeviceAlertEvents](advanced-hunting-migrate-from-mde.md#write-queries-without-devicealertevents).|
|[Centrum akcji](m365d-action-center.md)    | Lista oczekujących i ukończonych akcji, które zostały wykonane po zautomatyzowanych badaniach i działaniach naprawczych. Wcześniej Centrum akcji w centrum akcji w centrum akcji Centrum zabezpieczeń usługi Microsoft Defender się na liście oczekujących i ukończonych akcji dotyczących działań naprawczych podejmowane tylko na urządzeniach, a w przypadku automatycznego badania były wyświetlane alerty i stan. W ramach ulepszonej Microsoft 365 Defender akcji Centrum akcji łączy działania naprawcze i badania dotyczące poczty e-mail, urządzeń i użytkowników — wszystko w jednym miejscu.  |
| [Analiza zagrożeń](threat-analytics.md) |  Przeniesiono do górnej części paska nawigacyjnego w celu łatwiejszego odnajdowania i używania. Teraz zawiera informacje o zagrożeniach zarówno dla punktów końcowych, jak i poczty e-mail i współpracy.    |

### <a name="endpoints"></a>Punkty końcowe

| Obszar | Opis zmiany |
|---------|---------|
|Wyszukiwanie   |  Pasek wyszukiwania znajduje się w górnej części strony. Sugestie są udostępniane podczas pisania. W programie Defender można wyszukiwać w następujących jednostkach: Endpoint (Punkt końcowy) i Defender for Identity (Tożsamość): <br><br> - **Urządzenia** — obsługiwane zarówno dla usługi Defender for Endpoint, jak i Defender for Identity. Możesz nawet używać operatorów wyszukiwania, na przykład za pomocą operatora "zawiera" w celu wyszukania części nazwy hosta. <br><br> - **Użytkownicy** — obsługiwana zarówno w przypadku usługi Defender for Endpoint, jak i Defender for Identity. <br><br> - **Pliki, adresy IP i adresy URL —** te same funkcje, które są dostępne w programie Defender for Endpoint. <br> UWAGA: *Wyszukiwania adresów IP i URL są zgodne z dokładnym dopasowaniem i nie są wyświetlane na stronie wyników wyszukiwania — prowadzą bezpośrednio do strony encji.  <br><br> - **Program tvm** — te same funkcje, które są dostępne w programie Defender dla punktu końcowego (luki w zabezpieczeniach, oprogramowaniu i zaleceniach). <br><br>  Strona rozszerzonych wyników wyszukiwania scentralizować wyniki ze wszystkich jednostek.  |
|[Pulpit nawigacyjny](/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard)   |  To jest pulpit nawigacyjny operacji zabezpieczeń. Zapoznaj się z omówieniem ile aktywnych alertów zostało wyzwolono, które urządzenia są zagrożenia, którzy użytkownicy są zagrożenia, oraz poziomu ważności dla alertów, urządzeń i użytkowników. Możesz również sprawdzić, czy w jakimkolwiek urządzeniu nie ma problemów z czujnikiem, ogólną kondycją usługi i w jaki sposób wykryto wszelkie nierozpoznane alerty. |
|Spis urządzeń | Brak zmian. |
|[Zarządzanie lukami w zabezpieczeniach](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)    |    Nazwa została skrócona, aby zmieściła się w okienku nawigacji. Jest on taki sam jak sekcja Zarządzanie zagrożeniami i lukami, ze wszystkimi stronami poniżej.     |
| Partnerzy i interfejsy API | Brak zmian. |
| Oceny & samouczków    |     Nowe funkcje testowania i nauki.     |
| Zarządzanie konfiguracją   |  Brak zmian.  |

> [!NOTE]
> **Automatyczne badanie i rozwiązywanie problemów** jest teraz częścią zdarzeń. Zdarzenia automatycznego badania i rozwiązywania problemów można wyświetlić na karcie > **w śledztwie** .

> [!TIP]
> Wyszukiwanie urządzeń odbywa się z punktu końcowego > wyszukiwania.

### <a name="access-and-reporting"></a>Dostęp i raportowanie

| Obszar | Opis zmiany |
|---------|---------|
| Raporty  | Zobacz raporty dotyczące punktów końcowych i wiadomości e-&, w tym ochrony przed zagrożeniami, kondycji i zgodności urządzeń oraz narażona na zagrożenia. |
| Kondycja  |  Obecnie prowadzi do strony "Kondycja usługi" [w Centrum administracyjne platformy Microsoft 365.](https://admin.microsoft.com/) |
| Ustawienia |  Zarządzaj ustawieniami usługi Microsoft 365 Defender, punktów końcowych, współpracy & e-mail, tożsamości i odnajdowania urządzeń.   |

## <a name="microsoft-365-security-navigation-and-capabilities"></a>Microsoft 365 nawigacji i możliwości zabezpieczeń

Pasek nawigacji po lewej stronie (pasek Szybkie uruchamianie) będzie wyglądać znajomo. W portalu jest jednak kilka nowych i zaktualizowanych Microsoft 365 Defender elementów. 

### <a name="incidents-and-alerts"></a>Zdarzenia i alerty

Łączy zarządzanie zdarzeniami i alertami w wiadomościach e-mail, urządzeniach i tożsamościach. Strona alertu udostępnia pełny kontekst do alertu przez połączenie sygnałów ataków w celu skonstruowania szczegółowej historii. Nowe, ujednolicone środowisko zapewnia teraz spójny widok alertów dla różnych obciążeń. Możesz szybko przeprowadzić triage, zbadać i podjąć skuteczne działania.

- [Dowiedz się więcej o zdarzeniach](incidents-overview.md)
- [Dowiedz się więcej o zarządzaniu alertami](investigate-alerts.md)

:::image type="content" source="../../media/converge-1-alerts-and-actions.png" alt-text="Pasek szybkie uruchamianie Alerty i akcje w portalu Microsoft 365 Defender wiadomości" lightbox="../../media/converge-1-alerts-and-actions.png":::

### <a name="hunting"></a>Goniące

Aktywne wyszukiwanie zagrożeń, złośliwego oprogramowania i złośliwych działań w punktach końcowych, Office 365 skrzynkach pocztowych i nie tylko przy użyciu [zaawansowanych zapytań wyszukiwania](advanced-hunting-overview.md). Za pomocą tych zaawansowanych zapytań można lokalizować i przeglądać wskaźniki zagrożeń i jednostki zarówno dla znanych, jak i potencjalnych zagrożeń.

[Niestandardowe reguły wykrywania](custom-detection-rules.md) można utworzyć na pomocą zaawansowanych zapytań wyszukiwania, aby aktywnie obserwować zdarzenia, które mogą być chwycone przez naruszenie działań i nieprawidłowo skonfigurowane urządzenia.


### <a name="action-center"></a>Centrum akcji

Centrum akcji pokazuje badania utworzone na podstawie zautomatyzowanych możliwości badania i odpowiedzi. Ten zautomatyzowany, samoobsługowy program Microsoft 365 Defender pomaga zespołom zabezpieczeń, automatycznie odpowiadając na określone zdarzenia.

[Dowiedz się więcej o Centrum akcji](m365d-action-center.md).

### <a name="threat-analytics"></a>Analiza zagrożeń

Uzyskaj analizę zagrożeń od ekspertów od specjalistów ds. zabezpieczeń firmy Microsoft. Analiza zagrożeń pomaga zespołom zabezpieczeń zwiększyć efektywność w przypadku wyłaniających się zagrożeń. Analiza zagrożeń obejmuje:

- Wykrywanie i środki zaradcze związane z pocztą e-mail Ochrona usługi Office 365 w usłudze Microsoft Defender. Jest to dodatek do danych punktu końcowego, które są już dostępne w Ochrona punktu końcowego w usłudze Microsoft Defender.
- Widok zdarzeń związanych z zagrożeniami.
- Ulepszone środowisko do szybkiego identyfikowania i używania informacji z możliwością działania w raportach.

Do analizy zagrożeń możesz uzyskać dostęp z lewego górnego paska nawigacyjnego w aplikacji Microsoft 365 Defender lub z dedykowanej karty pulpitu nawigacyjnego, która pokazuje najważniejsze zagrożenia dla organizacji.

Dowiedz się więcej na temat śledzenia wyłaniających się zagrożeń i reagowania na [nie za pomocą analizy zagrożeń](./threat-analytics.md).

### <a name="endpoints-section"></a>Sekcja Punkty końcowe

Wyświetlaj zabezpieczenia punktów końcowych w organizacji i zarządzaj nimi. Jeśli używasz tego Centrum zabezpieczeń usługi Microsoft Defender, będzie ona wyglądać znajomo.

:::image type="content" source="../../media/converge-2-endpoints.png" alt-text="Pasek Szybkie uruchamianie punktów końcowych w portalu Microsoft 365 Defender sieci Web" lightbox="../../media/converge-2-endpoints.png":::

### <a name="access-and-reports"></a>Program Access i raporty

Wyświetlaj raporty, zmieniaj ustawienia i modyfikuj role użytkowników.

:::image type="content" source="../../media/converge-4-access-and-reporting-new.png" alt-text="Pasek szybkiego dostępu i raportowania w portalu Microsoft 365 Defender sieci" lightbox="../../media/converge-4-access-and-reporting-new.png":::

### <a name="siem-api-connections"></a>Połączenia interfejsu API SIEM

Jeśli korzystasz z [interfejsu API SIEM usługi Defender for Endpoint](../defender-endpoint/enable-siem-integration.md), możesz to robić w dalszym ciągu. Dodaliśmy nowe linki na ładowarce interfejsu API, które wskazują stronę alertu lub stronę zdarzenia w portalu Microsoft 365 zabezpieczeń. Nowe pola interfejsu API obejmują łącza LinkToMTP i IncidentLinkToMTP. Aby uzyskać więcej informacji, [zobacz Przekierowywanie kont z Ochrona punktu końcowego w usłudze Microsoft Defender do Microsoft 365 Defender](./microsoft-365-security-mde-redirection.md).

### <a name="email-alerts"></a>Alerty e-mail

Nadal możesz korzystać z alertów poczty e-mail dla usługi Defender dla punktu końcowego. Dodaliśmy nowe linki w wiadomościach e-mail, które wskazują stronę alertu lub stronę zdarzenia w aplikacji Microsoft 365 Defender. Aby uzyskać więcej informacji, [zobacz Przekierowywanie kont z Ochrona punktu końcowego w usłudze Microsoft Defender do Microsoft 365 Defender](./microsoft-365-security-mde-redirection.md).

### <a name="managed-security-service-providers-mssp"></a>Dostawcy zarządzanych usług zabezpieczeń (MSSP)

Logowanie się do wielu dzierżaw jednocześnie w tej samej sesji przeglądania nie jest obecnie obsługiwane w ujednoliconym portalu. Możesz zrezygnować z automatycznego przekierowywania, wracając do poprzedniego portalu [Ochrona punktu końcowego w usłudze Microsoft Defender, aby](microsoft-365-security-mde-redirection.md#can-i-go-back-to-using-the-former-portal) zachować tę funkcję do czasu rozwiązania problemu.

## <a name="related-information"></a>Informacje pokrewne

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender w programie Microsoft 365 Defender](microsoft-365-security-center-mde.md)
- [Przekierowywanie kont z Ochrona punktu końcowego w usłudze Microsoft Defender do Microsoft 365 Defender](microsoft-365-security-mde-redirection.md)
