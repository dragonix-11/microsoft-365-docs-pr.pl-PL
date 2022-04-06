---
title: Wprowadzenie przy użyciu portalu Microsoft 365 Defender
description: Zobacz, jak rozpocząć korzystanie z portalu Microsoft 365 Defender. Dowiedz się, jak nawigować po portalu i wyświetlać bieżący stan zabezpieczeń i zalecenia
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.custom: intro-get-started
ms.openlocfilehash: c5a940676eab6ae3a07c526ecb1bd910ed8751fe
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64667147"
---
# <a name="get-started-using-the-microsoft-365-defender-portal"></a>Wprowadzenie przy użyciu portalu Microsoft 365 Defender

> [!IMPORTANT]
> Microsoft Defender dla Firm jest wdrażana dla [klientów Microsoft 365 Business Premium](../../business-premium/index.md) od 1 marca 2022 r. Usługa Defender dla Firm jako subskrypcja autonomiczna jest dostępna w wersji zapoznawczej i będzie stopniowo wdrażana dla klientów i partnerów IT, którzy [zarejestrują się tutaj](https://aka.ms/mdb-preview) , aby zażądać tej subskrypcji. Wersja zapoznawcza zawiera [początkowy zestaw scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a my będziemy regularnie dodawać możliwości.
> 
> Niektóre informacje zawarte w tym artykule odnoszą się do wstępnie wydanych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjnym wydaniem. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, dotyczących informacji podanych tutaj. 

Po zarejestrowaniu się w Microsoft Defender dla Firm warto zapoznać się z portalem Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Ten artykuł zawiera następujące sekcje:

- [Jak nawigować po portalu Microsoft 365 Defender](#navigate-the-microsoft-365-defender-portal)

- [Edukacja moduły dotyczące zdarzeń i akcji reagowania](#complete-a-learning-module-about-incidents-and-response-actions) 

- [Następne kroki](#next-steps)

>
> **Masz minutę?**
> Weźmy <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę dotyczącą Microsoft Defender dla Firm</a>. Chcielibyśmy usłyszeć od Ciebie!
>

## <a name="navigate-the-microsoft-365-defender-portal"></a>Nawigowanie po portalu Microsoft 365 Defender

Portal Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) to punkt obsługi do korzystania z Microsoft Defender dla Firm i zarządzania nimi. Zawiera baner powitalny i objaśnienia ułatwiające rozpoczęcie pracy, karty, które udostępniają odpowiednie informacje, oraz pasek nawigacyjny, który zapewnia łatwy dostęp do różnych funkcji i możliwości.
 
Poświęć chwilę na zapoznanie się z portalem Microsoft 365 Defender.

:::image type="content" source="../../media/defender-business/mdb-portal-home.png" alt-text="portal Microsoft 365 Defender":::

### <a name="use-the-navigation-bar"></a>Korzystanie z paska nawigacyjnego

Użyj paska nawigacyjnego po lewej stronie ekranu, aby uzyskać dostęp do zdarzeń, wyświetlić raporty i zarządzać zasadami zabezpieczeń. W poniższej tabeli opisano elementy widoczne na pasku nawigacyjnym.

| Element | Opis |
|:---|:---|
| **Strona główna** | Spowoduje to przejście do strony głównej w Microsoft 365 Defender. Strona główna zawiera karty z wyróżnionymi aktywnymi zagrożeniami, które zostały wykryte, oraz zalecenia ułatwiające zabezpieczenie danych i urządzeń firmy. <br/><br/>Rekomendacje są zawarte w usłudze Defender for Business, mogą zaoszczędzić czas i nakład pracy zespołu ds. zabezpieczeń. Rekomendacje są oparte na najlepszych rozwiązaniach branżowych. Aby dowiedzieć się więcej na temat zaleceń, zobacz [Zalecenia dotyczące zabezpieczeń — Zarządzanie zagrożeniami i lukami](../defender-endpoint/tvm-security-recommendation.md). |
| **Zdarzenia** | Spowoduje to przejście do listy ostatnich zdarzeń. W miarę wyzwalania alertów tworzone są zdarzenia. Zdarzenie może zawierać wiele alertów. Pamiętaj, aby regularnie przeglądać zdarzenia. <br/><br/>Aby dowiedzieć się więcej o zdarzeniach, zobacz [Wyświetlanie zdarzeń i zarządzanie nimi w Microsoft Defender dla Firm](mdb-view-manage-incidents.md).|
| **Centrum akcji** | Spowoduje to przejście do listy akcji odpowiedzi, w tym zakończonych lub oczekujących akcji. <br/>— Wybierz kartę **Historia** , aby wyświetlić podjęte akcje. Niektóre akcje są wykonywane automatycznie; inne są wykonywane ręcznie lub ukończone po ich zatwierdzeniu. <br/>— Wybierz kartę **Oczekujące** , aby wyświetlić akcje wymagające zatwierdzenia. <br/><br/>Aby dowiedzieć się więcej na temat Centrum akcji, zobacz [Przeglądanie akcji korygowania w Centrum akcji](mdb-review-remediation-actions.md). |
| **Analiza zagrożeń** | Pozwala zapoznać się z bieżącymi zagrożeniami i zapewnia wgląd w krajobraz zagrożeń. Analiza zagrożeń obejmuje również raporty i informacje od badaczy zabezpieczeń firmy Microsoft. <br/><br/>Aby dowiedzieć się więcej na temat analizy zagrożeń, zobacz [Śledzenie pojawiających się zagrożeń i reagowanie na nie za pośrednictwem analizy zagrożeń](../defender-endpoint/threat-analytics.md). |
| **Wskaźnik bezpieczeństwa** | Zapewnia reprezentację pozycji bezpieczeństwa twojej firmy i oferuje sugestie, aby ją ulepszyć.<br/><br/>Aby dowiedzieć się więcej na temat wskaźnika bezpieczeństwa, zobacz [Wskaźnik bezpieczeństwa firmy Microsoft dla urządzeń](../defender-endpoint/tvm-microsoft-secure-score-devices.md). |
| **centrum Edukacja** | Zapewnia dostęp do szkoleń dotyczących zabezpieczeń i innych zasobów za pośrednictwem ścieżek szkoleniowych dołączonych do Subskrypcji. Możesz filtrować według produktu, poziomu umiejętności, roli i innych elementów. Centrum Edukacja może pomóc zespołowi ds. zabezpieczeń w zakresie funkcji zabezpieczeń & możliwości w usłudze Defender dla Firm i innych ofert firmy Microsoft, takich jak [Ochrona punktu końcowego w usłudze Microsoft Defender](../defender-endpoint/microsoft-defender-endpoint.md) i [ Ochrona usługi Office 365 w usłudze Microsoft Defender](../office-365-security/defender-for-office-365.md).  |
| **Punkty końcowe** >  **Szukaj** | Umożliwia wyszukiwanie co najmniej jednego urządzenia, które zostało dołączone do Microsoft Defender dla Firm. |
| **Punkty końcowe** >  **Spis urządzeń** | Umożliwia wyszukiwanie co najmniej jednego urządzenia, które zostało dołączone do Microsoft Defender dla Firm. |
| **Punkty końcowe** >  **Zarządzanie lukami w zabezpieczeniach** | Udostępnia pulpit nawigacyjny, rekomendacje, działania korygujące, spis oprogramowania i listę potencjalnych słabych stron w firmie. |
| **Punkty końcowe** >  **Samouczki** | Zapewnia dostęp do przewodników i symulacji, aby dowiedzieć się więcej o sposobie działania funkcji ochrony przed zagrożeniami. <br/><br/>Przed podjęciem próby pobrania pliku symulacji dla każdego **samouczka** wybierz link Przeczytaj przewodnik. Niektóre symulacje wymagają Office aplikacji, takich jak Microsoft Word, aby przeczytać przewodnik. |
| **Punkty końcowe** >  **Konfiguracja urządzenia** | Wyświetla listę zasad zabezpieczeń według systemu operacyjnego i typu. <br/><br/>Aby dowiedzieć się więcej na temat zasad zabezpieczeń, zobacz [Wyświetlanie lub edytowanie zasad w Microsoft Defender dla Firm](mdb-view-edit-policies.md). |
| **Raporty** | Wyświetla listę dostępnych raportów zabezpieczeń. Te raporty umożliwiają wyświetlanie trendów zabezpieczeń, wyświetlanie szczegółowych informacji o wykrywaniu zagrożeń i alertach oraz uzyskiwanie dodatkowych informacji o urządzeniach firmy narażonych na zagrożenia. |
| **Kondycja** | Umożliwia wyświetlanie stanu kondycji usługi i planowanie nadchodzących zmian. <br/>— Wybierz **pozycję Kondycja usługi**, aby wyświetlić stan kondycji usług Microsoft 365 uwzględnionych w subskrypcji firmy. <br/>— Wybierz pozycję **Centrum komunikatów** , aby dowiedzieć się więcej o planowanych zmianach i oczekiwaniach.  |
| **Uprawnienia & ról** | Umożliwia przypisywanie uprawnień osobom w firmie, które będą zarządzać zabezpieczeniami oraz wyświetlać zdarzenia i raporty w portalu Microsoft 365 Defender. Umożliwia również konfigurowanie grup urządzeń i zarządzanie nimi w celu dołączania urządzeń firmy i przypisywania zasad ochrony przed zagrożeniami.  |
| **Ustawienia** | Umożliwia edytowanie ustawień portalu Microsoft 365 Defender i Microsoft Defender dla Firm. Na przykład możesz dołączyć (lub odłączyć) i urządzenia firmy (nazywane również punktami końcowymi). Można również zdefiniować reguły, takie jak reguły pomijania alertów, i skonfigurować wskaźniki do blokowania lub zezwalania na niektóre pliki lub procesy.  |
| **Więcej zasobów** | Przejdź do innych portali, takich jak Azure Active Directory. Pamiętaj, że portal Microsoft 365 Defender powinien spełniać Twoje potrzeby bez konieczności przechodzenia do innych portali. |

## <a name="complete-a-learning-module-about-incidents-and-response-actions"></a>Ukończenie modułu szkoleniowego dotyczącego zdarzeń i akcji reagowania

Zapoznaj się z modułem szkoleniowym [Wykrywanie problemów z zabezpieczeniami i reagowanie na nie](/learn/modules/m365-detect-respond-security-issues-defender-endpoint/), aby uzyskać przegląd zdarzeń i akcji reagowania. Poznasz kolejkę zdarzeń, alerty i akcje reagowania, które możesz wykonać. Ten kurs pomoże Ci rozpocząć pracę z incydentami w usłudze Defender dla Firm.

> [!NOTE]
> Mimo że moduł szkoleniowy ([Wykrywanie problemów z zabezpieczeniami i reagowanie na nie](/learn/modules/m365-detect-respond-security-issues-defender-endpoint/)) jest faktycznie przeznaczony dla Ochrona punktu końcowego w usłudze Microsoft Defender, podstawowe pojęcia i ogólny przepływ są podobne do tych, które zobaczysz w usłudze Defender for Business.

## <a name="next-steps"></a>Następne kroki

Teraz, gdy masz omówienie usługi Defender dla Firm, spróbuj wykonać co najmniej jedno z następujących zadań:

- [Wypróbuj samouczki i symulacje w Microsoft Defender dla Firm](mdb-tutorials.md)

- [Zarządzanie urządzeniami w Microsoft Defender dla Firm](mdb-manage-devices.md)

- [Wyświetlanie zdarzeń i zarządzanie nimi w Microsoft Defender dla Firm](mdb-view-manage-incidents.md)

- [Reagowanie na zagrożenia w Microsoft Defender dla Firm i eliminowanie ich](mdb-respond-mitigate-threats.md)

- [Przeglądanie akcji korygowania w centrum akcji](mdb-review-remediation-actions.md)

- [Wyświetlanie lub edytowanie zasad w Microsoft Defender dla Firm](mdb-view-edit-policies.md)