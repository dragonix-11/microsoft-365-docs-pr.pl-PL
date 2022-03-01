---
title: Co nowego w programie Microsoft 365 Defender
description: Lista nowych funkcji w programie Microsoft 365 Defender
keywords: co nowego w programie Microsoft 365 Defender, ga, ogólnie dostępne, funkcje, dostępne, nowe
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: edaa7398b8d3213479c9b81af248b928f7b3f3e0
ms.sourcegitcommit: f8267a0860de62dbd53ebb8a151a8e71a8ccda6a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2022
ms.locfileid: "63016057"
---
# <a name="whats-new-in-microsoft-365-defender"></a>Co nowego w programie Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

> Chcesz doświadczyć Microsoft 365 Defender? Można go [ocenić w środowisku laboratoryjnym](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) lub [uruchomić projekt pilotażowy w środowisku produkcyjnym](m365d-pilot.md?ocid=cx-evalpilot).

Poniższe funkcje są dostępne w wersji zapoznawczej lub ogólnie dostępne w najnowszej wersji programu Microsoft 365 Defender.

Kanał informacyjny RSS: Otrzymuj powiadomienia o aktualizacji tej strony, kopiując i wklejając następujący adres URL do czytnika kanału informacyjnego:

```http
https://docs.microsoft.com/api/search/rss?search=%22Lists+the+new+features+and+functionality+in+Microsoft+365+defender%22&locale=en-us
```

Aby uzyskać więcej informacji o nowościach w innych produktach zabezpieczeń Microsoft Defender, zobacz:

- [Co nowego w programie Microsoft Defender dla systemu Office 365](../office-365-security/whats-new-in-defender-for-office-365.md)
- [Co nowego w programie Microsoft Defender dla punktu końcowego](../defender-endpoint/whats-new-in-microsoft-defender-endpoint.md)
- [Co nowego w programie Microsoft Defender dla tożsamości](/defender-for-identity/whats-new)
- [Co nowego w programie Microsoft Defender dla aplikacji w chmurze](/cloud-app-security/release-notes)

Za pośrednictwem centrum wiadomości możesz również otrzymywać aktualizacje produktów i ważne [powiadomienia](https://admin.microsoft.com/Adminportal/Home#/MessageCenter). 

## <a name="december-2021"></a>Grudzień 2021

- (GA) Tabela `DeviceTvmSoftwareEvidenceBeta` została dodana przez krótki czas w celu szukania informacji na temat tego, gdzie określone oprogramowanie zostało wykryte na urządzeniu.

## <a name="november-2021"></a>Listopad 2021

- (Wersja zapoznawcza) Funkcja dodatku do zarządzania aplikacjami aplikacji Defender dla chmury jest teraz dostępna w Microsoft 365 Defender. Zarządzanie aplikacjami zapewnia funkcję zarządzania zabezpieczeniami i zasadami opracowaną dla aplikacji z obsługą protokołu OAuth, które mają Microsoft 365 dostępu do danych za pośrednictwem interfejsów API Graph Microsoft. Zarządzanie aplikacjami zapewnia pełną widoczność, działania naprawcze i zarządzanie tym, w jaki sposób te aplikacje i ich użytkownicy mają dostęp do Twoich poufnych danych przechowywanych w programie Microsoft 365 i udostępniaj je, udostępniając szczegółowe informacje oraz automatyczne alerty i działania zasad, a także zapewniają dostęp do nich. [Dowiedz się więcej o zarządzaniu aplikacją](/cloud-app-security/app-governance-manage-app-governance).
- (Wersja zapoznawcza) [Zaawansowana](advanced-hunting-overview.md) strona wyszukiwania ma teraz obsługę wielostronicową, inteligentne przewijanie, usprawnione karty schematów, opcje szybkiego edytowania zapytań, wskaźnik użycia zasobów zapytań i inne ulepszenia usprawniające i bardziej precyzyjne wykonywanie zapytań.
- (Wersja zapoznawcza) Teraz możesz użyć linku [](advanced-hunting-link-to-incident.md) do funkcji zdarzenia, aby dołączyć zdarzenia lub rekordy z zaawansowanych zapytań wyszukiwania bezpośrednio do nowego lub istniejącego zdarzenia, które badasz.

## <a name="october-2021"></a>Październik 2021

- (GA) Podczas zaawansowanego wyszukiwania w tabeli [CloudAppEvents dodano więcej](advanced-hunting-cloudappevents-table.md) kolumn. Teraz możesz uwzględnić `AccountType`, `IsExternalUser`, `IsImpersonated`, `IPTags`, `IPCategory`i do `UserAgentTags` swoich zapytań.

## <a name="september-2021"></a>Wrzesień 2021

- (GA) Program Microsoft Defender for Office 365 danych zdarzeń jest dostępny w interfejsie API przesyłania strumieniowego Microsoft 365 Defender zdarzeń. Dostępność i stan typów zdarzeń można sprawdzić w obsługiwanych typach zdarzeń Microsoft 365 Defender [interfejsie API przesyłania strumieniowego](supported-event-types.md).
- (GA) Program Microsoft Defender for Office 365 data available in advanced hunting is now general available.
- (GA) Przypisywanie zdarzeń i alertów do kont użytkowników

  Do konta użytkownika możesz przypisać zdarzenie i wszystkie skojarzone z nim alerty, w okienku Zarządzaj zdarzeniem w okienku Zarządzanie  zdarzeniem lub Zarządzanie **alertem**.

## <a name="august-2021"></a>Sierpień 2021

- (Wersja zapoznawcza) Program Microsoft Defender do Office 365 danych dostępnych podczas szukania zaawansowanego

  Nowe kolumny w tabelach wiadomości e-mail mogą zapewniać więcej informacji o zagrożeniach opartych na wiadomościach e-mail, co zapewnia dokładniejszą analizę przy użyciu zaawansowanych narzędzi do wyszukiwania. Teraz możesz uwzględnić kolumnę w `AuthenticationDetails` tabelach [EmailEvents](./advanced-hunting-emailevents-table.md), `FileSize` [EmailAttachmentInfo](./advanced-hunting-emailattachmentinfo-table.md)`ThreatTypes` `DetectionMethods` i [EmailPostDeliveryEvents](./advanced-hunting-emailpostdeliveryevents-table.md).

- (Wersja zapoznawcza) Wykres zdarzeń

  Nowa **karta Graph** na karcie Podsumowanie zdarzenia pokazuje pełny  zakres ataków, sposób rozsuńenia ataków w sieci w czasie, miejsce jego rozpoczęcia i zakres działań atakujących.

## <a name="july-2021"></a>Lipiec 2021

- [Professional usług firmy Microsoft](https://sip.security.microsoft.com/interoperability/professional_services)

  Ulepsz możliwości wykrywania, analizy i analizy zagrożeń na platformie dzięki obsługiwanym kontaktom partnerów.

## <a name="june-2021"></a>Czerwiec 2021

- (Wersja zapoznawcza) [Wyświetlanie raportów według tagów zagrożeń](threat-analytics.md#view-reports-per-threat-tags)

  Tagi zagrożeń ułatwiają skoncentrowanie się na określonych kategoriach zagrożeń i przeglądanie najbardziej odpowiednich raportów.

- (Wersja zapoznawcza) [Interfejs API przesyłania strumieniowego](../defender-endpoint/raw-data-export.md)

  Microsoft 365 Defender obsługuje przesyłanie strumieniowe wszystkich wydarzeń dostępnych za pośrednictwem zaawansowanego wyszukiwania do centrum wydarzeń i/lub konta magazynu platformy Azure.

- (Wersja zapoznawcza) [Weź udział w zaawansowanym chłonie](advanced-hunting-take-action.md)

  Szybko zawieraj zagrożenia lub zaadresuj naruszone zasoby, które znajdziesz podczas [zaawansowanego szukania](advanced-hunting-overview.md).

- (Wersja zapoznawcza) [Informacje o schemacie w portalu](advanced-hunting-schema-tables.md#get-schema-information-in-the-security-center)

  Uzyskaj informacje na temat zaawansowanych tabel schematu chłoniania bezpośrednio w centrum zabezpieczeń. Oprócz opisów tabel i kolumn takie odwołanie obejmuje obsługiwane typy zdarzeń (`ActionType` wartości) i przykładowe zapytania.

- (Wersja zapoznawcza) [DeviceFromIP()](advanced-hunting-devicefromip-function.md)

  Uzyskaj informacje o urządzeniach, do których przypisano określony adres IP lub adresy w danym zakresie czasu.

## <a name="may-2021"></a>Maj 2021

- [Strona nowego alertu w portalu Microsoft 365 Defender sieci Web](https://techcommunity.microsoft.com/t5/microsoft-365-defender/easily-find-anomalies-in-incidents-and-alerts/ba-p/2339243)

  Zapewnia rozszerzone informacje o kontekście podczas ataków. Możesz zobaczyć, który inny alert wyzwalany spowodował bieżący alert oraz wszystkie jednostki i działania, których dotyczy atak, w tym pliki, użytkowników i skrzynki pocztowe. Aby [uzyskać więcej informacji,](/microsoft-365/security/defender/investigate-alerts) zobacz Badanie alertów.

- [Wykres trendu dla zdarzeń i alertów w portalu Microsoft 365 Defender informacje](https://techcommunity.microsoft.com/t5/microsoft-365-defender/new-alert-page-for-microsoft-365-defender-incident-detections/ba-p/2350425)

  Określ, czy istnieje kilka alertów dotyczących pojedynczego zdarzenia lub że Twoja organizacja jest w trakcie ataków w przypadku kilku różnych zdarzeń. Aby [uzyskać więcej informacji, zobacz Określanie priorytetów](/microsoft-365/security/defender/incident-queue) zdarzeń.

## <a name="april-2021"></a>Kwiecień 2021

- Microsoft 365 Defender

  Ulepszona [Microsoft 365 Defender](https://security.microsoft.com) jest teraz dostępna. To nowe środowisko łączy funkcje Defender for Endpoint (Punkt końcowy), Defender for Office 365 for Office 365 (Defender for Identity) i (nie tylko) w jeden portal. To nowa dom do zarządzania mechanizmami kontroli zabezpieczeń. [Dowiedz się, co nowego](./microsoft-365-defender.md#the-microsoft-365-defender-portal).

- [Microsoft 365 Defender raportu analizy zagrożeń](threat-analytics.md)

  Analiza zagrożeń ułatwia reagowanie i minimalizowanie wpływu aktywnych ataków. Możesz również dowiedzieć się więcej o próbach ataków zablokowanych przez firmy Microsoft 365 Defender i podejmować działania działańczych, które złagodnią ryzyko dalszego kontaktu z ryzykiem oraz zwiększają odporność. W ramach ujednoliconego systemu zabezpieczeń analiza zagrożeń jest teraz dostępna dla programu Microsoft Defender dla punktów końcowych i programu Microsoft Defender dla posiadaczy licencji Office E5.

## <a name="march-2021"></a>Marzec 2021 r.

- [Tabela CloudAppEvents](advanced-hunting-cloudappevents-table.md)

  Znajdowanie informacji o wydarzeniach w różnych aplikacjach i usługach w chmurze objętych Microsoft Cloud App Security. Ta tabela zawiera również informacje dostępne wcześniej w `AppFileEvents` tabeli.

## <a name="february-2021"></a>Luty 2021 r.

- (Wersja zapoznawcza) Rozszerzony Microsoft 365 Defender [(https://security.microsoft.com)](https://security.microsoft.com)jest teraz dostępny w publicznej wersji Preview. To nowe środowisko wprowadza w centrum funkcje: Defender for Endpoint Office 365 Defender. [Dowiedz się więcej o tym, co się zmieniło](microsoft-365-defender.md#the-microsoft-365-defender-portal).

- **[(Preview) Microsoft 365 Defender API](api-overview.md)** — interfejsy API Microsoft 365 Defender najwyższego poziomu umożliwiają automatyzowanie przepływów pracy na podstawie udostępnionych zdarzeń i zaawansowanych tabel chłoń.
