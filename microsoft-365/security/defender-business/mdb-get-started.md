---
title: Rozpoczynanie korzystania z portalu Microsoft 365 Defender-
description: Zobacz, jak rozpocząć korzystanie z Microsoft 365 Defender usługi. Dowiedz się, jak poruszać się po portalu oraz wyświetlać bieżący stan zabezpieczeń i zalecenia
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 02/07/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.custom: intro-get-started
ms.openlocfilehash: 15fbed00484497c7d1dd9f8fa217529bddc1cf51
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2022
ms.locfileid: "63016547"
---
# <a name="get-started-using-the-microsoft-365-defender-portal"></a>Rozpoczynanie korzystania z portalu Microsoft 365 Defender-

> [!IMPORTANT]
> Usługa Microsoft Defender dla firm jest teraz w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, którzy zarejestrują się tutaj [, aby](https://aka.ms/mdb-preview) poprosić o to. W najbliższych tygodniach nawiązemy wstępną ofertę klientów i partnerów oraz rozszerzymy jej wersja zapoznawczą, aby rozszerzyć jej dostępność do ogólnej dostępności. Pamiętaj, że wersja Preview zostanie uruchamiana z [początkowym zestawem scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a funkcje będą regularnie dodajemy.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

Po zalogowaniu się do usługi Microsoft Defender dla firm (wersja Preview) możesz zapoznać się z portalem Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Ten artykuł zawiera następujące sekcje:

- [Jak nawigować po Microsoft 365 Defender portalu](#navigate-the-microsoft-365-defender-portal)
- [Edukacja na temat zdarzeń i akcji reagowania](#complete-a-learning-module-about-incidents-and-response-actions) 
- [Następne kroki](#next-steps)

>
> **Masz minutę?**
> Prosimy o <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę na temat programu Microsoft Defender dla firm</a>. Chcemy ją usłyszeć!
>

## <a name="navigate-the-microsoft-365-defender-portal"></a>Poruszanie się Microsoft 365 Defender portalu

Portal Microsoft 365 Defender () to jedno zatrzymanie pracy przy użyciu programu Microsoft Defender dla firm ([https://security.microsoft.com](https://security.microsoft.com)wersja Preview) i zarządzanie nimi. Zawiera transparent powitalny i objaśnienia, które ułatwiają rozpoczynanie pracy, karty, które zawierają istotne informacje, oraz pasek nawigacyjny, który zapewnia łatwy dostęp do różnych funkcji i możliwości.
 
Po chwili zapoznaj się z portalem informacyjnym, Microsoft 365 Defender portalem.

:::image type="content" source="../../media/defender-business/mdb-portal-home.png" alt-text="Microsoft 365 Defender portalu":::

### <a name="use-the-navigation-bar"></a>Korzystanie z paska nawigacyjnego

Użyj paska nawigacyjnego po lewej stronie ekranu, aby uzyskać dostęp do zdarzeń, wyświetlać raporty i zarządzać zasadami zabezpieczeń. W poniższej tabeli opisano elementy, które są zobaczyć na pasku nawigacyjnym.

| Element | Opis |
|:---|:---|
| **Strona główna** | Przenosi Cię do strony głównej w programie Microsoft 365 Defender. Strona główna zawiera karty z wyróżnieniami wykrytych aktywnych zagrożeń oraz zalecenia dotyczące zabezpieczania danych i urządzeń organizacji. <br/><br/>Rekomendacje są dostępne w programie Defender dla firm (wersja Preview) mogą zaoszczędzić czas i wysiłku zespołu zabezpieczeń. Rekomendacje są oparte na najlepszych rozwiązaniach branżowych. Aby dowiedzieć się więcej o zaleceniach, zobacz [Zalecenia dotyczące zabezpieczeń — Zarządzanie zagrożeniami i lukami](../defender-endpoint/tvm-security-recommendation.md). |
| **Zdarzenia** | Pozwala wyświetlić listę ostatnich zdarzeń. W przypadku wyzwalania alertów są tworzone zdarzenia. Zdarzenie może zawierać wiele alertów. Pamiętaj, aby regularnie przeglądać zdarzenia. <br/><br/>Aby dowiedzieć się więcej o incydentach, zobacz Wyświetlanie zdarzeń i zarządzanie nimi w [u programie Microsoft Defender dla firm (wersja zapoznawcza).](mdb-view-manage-incidents.md)|
| **Centrum akcji** | Umożliwia dostęp do listy akcji odpowiedzi, w tym akcji ukończonych lub oczekujących. <br/>— Wybierz **kartę** Historia, aby wyświetlić wykonane akcje. Niektóre akcje są podejmowane automatycznie. inne są wykonywane ręcznie lub ukończone po zatwierdzeniu. <br/>— Wybierz kartę **Oczekujące** , aby wyświetlić akcje wymagające zatwierdzenia w celu kontynuowania. <br/><br/>Aby dowiedzieć się więcej o Centrum akcji, zobacz [Przeglądanie działań naprawczych w Centrum akcji](mdb-review-remediation-actions.md). |
| **Analiza zagrożeń** | Pozwala spojrzeć na bieżące zagrożenia, a także pozwala jednym rzutem oka zobaczyć obszar zagrożeń. Analiza zagrożeń obejmuje również raporty i informacje od użytkowników zabezpieczeń firmy Microsoft. <br/><br/>Aby dowiedzieć się więcej na temat analizy zagrożeń, zobacz Śledzenie wyłaniających się zagrożeń i odpowiadanie [na nie za pomocą analizy zagrożeń](../defender-endpoint/threat-analytics.md). |
| **Secure score** | Zapewnia przedstawienie pozycji zabezpieczeń organizacji i oferuje sugestie, które można ulepszyć.<br/><br/>Aby dowiedzieć się więcej na temat bezpiecznego wyniku, zobacz [Wynik bezpiecznego wyniku firmy Microsoft dla urządzeń](../defender-endpoint/tvm-microsoft-secure-score-devices.md). |
| **Edukacja centrum** | Zapewnia dostęp do szkoleń zabezpieczeń i innych zasobów za pośrednictwem ścieżek nauki dołączonych do subskrypcji. Możesz filtrować według produktu, poziomu umiejętności, roli i nie tylko. Centrum Edukacja może ułatwić Zespołowi zabezpieczeń podjęcie pracy nad funkcjami zabezpieczeń & w programie Defender dla firm (wersja Preview) i w większej liczby ofertach firmy Microsoft, takich jak [Microsoft Defender for Endpoint](../defender-endpoint/microsoft-defender-endpoint.md) i [Microsoft Defender for Office 365](../office-365-security/defender-for-office-365.md).  |
| **Punkty końcowe** >  **Wyszukiwanie** | Umożliwia wyszukanie jednego lub większej liczby urządzeń, które zostały podłączone do usługi Microsoft Defender dla firm (wersja Preview). |
| **Punkty końcowe** >  **Spis urządzeń** | Umożliwia wyszukanie jednego lub większej liczby urządzeń, które zostały podłączone do usługi Microsoft Defender dla firm (wersja Preview). |
| **Punkty końcowe** >  **Zarządzanie lukami w zabezpieczeniach** | Udostępnia pulpit nawigacyjny, zalecenia, działania naprawcze, spis oprogramowania oraz listę potencjalnych problemów w organizacji. |
| **Punkty końcowe** >  **Samouczki** | Zapewnia dostęp do instruktaży i symulowań, aby dowiedzieć się więcej na temat działania funkcji ochrony przed zagrożeniami. <br/><br/>Przed **podjęciem próby uzyskania pliku symulacyjnego** dla każdego samouczka wybierz link Przeczytaj instruktaż. Niektóre symeony wymagają Office takich jak Microsoft Word, aby przeczytać instruktaż. |
| **Punkty końcowe** >  **Konfiguracja urządzenia** | Zawiera listę zasad zabezpieczeń według systemu operacyjnego i typu. <br/><br/>Aby dowiedzieć się więcej o zasadach zabezpieczeń, zobacz Wyświetlanie [i edytowanie zasad w programie Microsoft Defender dla firm (wersja Preview).](mdb-view-edit-policies.md) |
| **Raporty** | Zawiera listę dostępnych raportów zabezpieczeń. Raporty te pozwalają przeglądać trendy zabezpieczeń, wyświetlać szczegółowe informacje na temat wykrywania zagrożeń i alertów oraz dowiedzieć się więcej o urządzeniach, na których twoja organizacja jest podatna na zagrożenia. |
| **Kondycja** | Umożliwia wyświetlenie stanu kondycji usługi i zaplanowanie nadchodzących zmian. <br/>— Wybierz **pozycję Kondycja** usługi, aby wyświetlić stan kondycji Microsoft 365 usług uwzględnionych w subskrypcji Twojej organizacji. <br/>— Wybierz **pozycję Centrum wiadomości,** aby dowiedzieć się więcej na temat planowanych zmian i tego, czego można oczekiwać.  |
| **Uprawnienia & ról** | Umożliwia przypisywanie uprawnień do osób w organizacji, które będą zarządzać zabezpieczeniami oraz wyświetlać zdarzenia i raporty w portalu Microsoft 365 Defender sieci. Ponadto możesz skonfigurować grupy urządzeń i zarządzać nimi w celu wsadunia urządzeń organizacji na urządzenia i przypisywania zasad ochrony przed zagrożeniami.  |
| **Ustawienia** | Umożliwia edytowanie ustawień portalu usługi Microsoft 365 Defender oraz programu Microsoft Defender dla firm (wersja Preview). Na przykład możesz korzystać z aplikacji (lub aplikacji) i urządzeń organizacji (nazywanych również punktami końcowymi). Można również zdefiniować reguły, takie jak reguły alertów i skonfigurować wskaźniki blokowania lub zezwalania na określone pliki lub procesy.  |
| **Więcej zasobów** | Przejdź do innych portali, takich jak Azure Active Directory. Pamiętaj, że portal Microsoft 365 Defender powinien spełniać Twoje potrzeby bez konieczności przechodzenia do innych portali. |

## <a name="complete-a-learning-module-about-incidents-and-response-actions"></a>Ukończenie modułu szkoleniowego na temat zdarzeń i akcji reagowania

Zobacz moduł nauki Wykrywanie problemów [dotyczących](/learn/modules/m365-detect-respond-security-issues-defender-endpoint/) zabezpieczeń i odpowiadanie na nie, aby uzyskać przegląd zdarzeń i działań reagowania. Dowiesz się więcej o kolejkach zdarzeń, alertach i akcjach odpowiedzi, które możesz podjąć. Ten kurs pomoże Ci rozpocząć pracę nad zdarzeniami w programie Defender dla firm (wersja preview).

> [!NOTE]
> Chociaż moduł [nauki (Wykrywanie](/learn/modules/m365-detect-respond-security-issues-defender-endpoint/) problemów z zabezpieczeniami i odpowiadanie na nie) w rzeczywistości jest dla programu Microsoft Defender for Endpoint, podstawowe pojęcia i ogólny przepływ są podobne do tego, co widzisz w programie Defender dla firm (wersja Preview).

## <a name="next-steps"></a>Następne kroki

Teraz, gdy masz już omówienie programu Defender dla firm (wersja Preview), wypróbuj co najmniej jedno z następujących zadań:

- [Wypróbuj samouczki i symulowania w programie Microsoft Defender dla firm (wersja Preview)](mdb-tutorials.md)

- [Zarządzanie urządzeniami w programie Microsoft Defender dla firm (wersja preview)](mdb-manage-devices.md)

- [Wyświetlanie zdarzeń i zarządzanie nimi w programie Microsoft Defender dla firm (wersja Preview)](mdb-view-manage-incidents.md)

- [Reagowanie na zagrożenia i ograniczanie ich w programie Microsoft Defender dla firm (wersja Preview)](mdb-respond-mitigate-threats.md)

- [Przeglądanie działań naprawczych w Centrum akcji](mdb-review-remediation-actions.md)

- [Wyświetlanie i edytowanie zasad w programie Microsoft Defender dla firm (wersja Preview)](mdb-view-edit-policies.md)