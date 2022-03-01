---
title: Przegląd wymagań dotyczących architektury i struktury technicznej programu Microsoft Defender dla tożsamości
description: Diagram techniczny usługi Microsoft Defender for Identity w programie Microsoft 365 Defender pomaga zrozumieć tożsamość w programie Microsoft 365 przed rozpoczęciem tworzenia laboratorium próbnego lub środowiska pilotażowego.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 2569349bd5255f47ebca710263dfd7510aee817b
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63013387"
---
# <a name="review-architecture-requirements-and-key-concepts-for-microsoft-defender-for-identity"></a>Przegląd wymagań dotyczących architektury i kluczowych pojęć dotyczących usługi Microsoft Defender dla tożsamości


**Dotyczy:**
- Microsoft 365 Defender

Ten artykuł dotyczy [kroku 1 z 3](eval-defender-identity-overview.md) w procesie konfigurowania środowiska oceny dla programu Microsoft Defender dla tożsamości. Aby uzyskać więcej informacji na temat tego procesu, zobacz artykuł [z omówieniem](eval-defender-identity-overview.md).

Przed włączeniem programu Microsoft Defender dla tożsamości upewnij się, że rozumiesz architekturę i może spełniać wymagania.

Usługa Microsoft Defender for Identity używa uczenia maszynowego i analizy zachowania do identyfikowania ataków w Twojej sieci lokalnej oraz wykrywania i aktywnego zapobiegania ryzyku logowania użytkowników skojarzonym z tożsamościami w chmurze. Aby uzyskać więcej informacji, zobacz [Co to jest program Microsoft Defender dla tożsamości?](/defender-for-identity/what-is)

Usługa Defender for Identity chroni lokalnych użytkowników i/lub użytkowników usługi Active Directory zsynchronizowanych z usługą Azure Active Directory (Azure AD). Aby chronić środowisko składane tylko z użytkowników usługi Azure AD, zobacz [Usługa Azure AD Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection).

## <a name="understand-the-architecture"></a>Opis architektury

Na poniższym diagramie przedstawiono podstawową architekturę usługi Defender dla tożsamości. 

![Architektura programu Microsoft Defender dla tożsamości.](../../media/defender/m365-defender-identity-architecture.png)

Na poniższej ilustracji:
- Czujniki zainstalowane w kontrolerach domeny usługi AD analizują dzienniki i ruch sieciowy i wysyłają je do usługi Microsoft Defender for Identity w celu analizy i raportowania.
-  Czujniki mogą również  analizuje usługi federacyjne Active Directory (AD FS), jeśli usługa Azure AD jest skonfigurowana do korzystania z uwierzytelniania federacyjne (linia kropkowana na ilustracji). 
- Usługa Microsoft Defender for Identity udostępnia sygnały do Microsoft 365 Defender wykrywania rozszerzonego i odpowiedzi (XDR).


Czujnik usługi Defender for Identity można zainstalować bezpośrednio na następujących serwerach:

- Kontrolery domeny: Czujnik bezpośrednio monitoruje ruch kontrolera domeny bez konieczności użycia serwera dedykowanego ani konfiguracji dublowania portów.
- USŁUGI AD FS: Czujnik bezpośrednio monitoruje ruch sieciowy i zdarzenia uwierzytelniania.

Aby uzyskać bardziej szczegółowe informacje na temat architektury usługi Defender for Identity, w tym integracji z programem Defender dla aplikacji w chmurze, zobacz Architektura tożsamości programu [Microsoft Defender](/defender-for-identity/architecture).


## <a name="understand-key-concepts"></a>Opis kluczowych pojęć

W poniższej tabeli przedstawiono kluczowe pojęcia, które należy zrozumieć podczas oceniania, konfigurowania i wdrażania programu Microsoft Defender dla tożsamości.


|Pojęcie  |Opis |Więcej informacji  |
|---------|---------|---------|
| Monitorowane działania | Program Defender for Identity monitoruje sygnały wygenerowane w organizacji w celu wykrycia podejrzanych lub złośliwych działań, a także pomaga określić ważność każdego potencjalnego zagrożenia, co umożliwia skuteczne trygonstwo i reagowanie.  |  [Działania monitorowane w programie Microsoft Defender for Identity](/defender-for-identity/monitored-activities)       |
| Alerty zabezpieczeń    | Alerty zabezpieczeń usługi Defender for Identity wyjaśniają podejrzane działania wykrywane przez czujniki w twojej sieci wraz z szyciem i komputerami, których dotyczy każda zagrożenie.   | [Alerty zabezpieczeń usługi Microsoft Defender dla tożsamości](/defender-for-identity/suspicious-activity-guide?tabs=external)    |
| Profile encji    | Profile encji zapewniają kompleksowe badanie użytkowników, komputerów, urządzeń i zasobów wraz z ich historią dostępu.   | [Opis profilów encji](/defender-for-identity/entity-profiles)  |
| Ścieżki ruchu bocznego    | Kluczowym elementem szczegółowych informacji o zabezpieczeniach MDI jest zidentyfikowanie późniejszych ścieżek ruchu, w których atakujący używa kont nie poufnych w celu uzyskania dostępu do poufnych kont lub komputerów w twojej sieci.  | [Ścieżki ruchu bocznego usługi Microsoft Defender for Identity (LMPs)](/defender-for-identity/use-case-lateral-movement-path)  |
| Rozdzielczość nazw sieciowych    |  Funkcja rozpoznawania nazw sieci (NNR, Network Name Resolution) jest składnikiem funkcji MDI, która rejestruje działania na podstawie ruchu sieciowego, zdarzeń Windows, ETW itp. skoreluje te pierwotne dane z odpowiednimi komputerami zaangażowanymi w każde działanie.       | [Co to jest rozpoznawania nazw sieciowych?](/defender-for-identity/nnr-policy)      |
| Raporty    | Raporty usługi Defender dla tożsamości umożliwiają planowanie lub natychmiastowe generowanie i pobieranie raportów, które dostarczają informacje o stanie systemu i jednostki.  Możesz tworzyć raporty dotyczące kondycji systemu, alertów zabezpieczeń i potencjalnych ścieżek ruchu lateralnych wykrytych w środowisku.   | [Raporty tożsamości programu Microsoft Defender dla tożsamości ](/defender-for-identity/reports)       |
| Grupy ról    | Program Defender for Identity oferuje grupy oparte na rolach i dostęp delegowany w celu zabezpieczenia danych zgodnie z określonymi potrzebami organizacji w zakresie zabezpieczeń i zgodności, które obejmują administratorów, użytkowników i osoby przeglądowe.        |  [Grupy ról usługi Microsoft Defender dla tożsamości](/defender-for-identity/role-groups)       |
| Portal administracyjny    |  Oprócz portalu Microsoft 365 Defender cab portalu usługi Defender for Identity jest używane do monitorowania podejrzanych działań i reagowania na nie.      | [Praca z portalem usługi Microsoft Defender for Identity](/defender-for-identity/workspace-portal)        |
| Integracja programu Microsoft Defender dla aplikacji w chmurze   | Program Microsoft Defender for Cloud Apps integruje się z programem Microsoft Defender for Identity w celu zapewnienia analizy zachowań encji użytkownika (UEBA) w środowisku hybrydowym — zarówno w aplikacji w chmurze, jak i w środowisku lokalnym   | Integracja usługi Microsoft Defender dla tożsamości  |
| | | |


## <a name="review-prerequisites"></a>Przejrzyj wymagania wstępne

Do zapewnienia, że lokalna tożsamość i składniki sieciowe spełniają minimalne wymagania, wymaga pewnych wstępnych prac usługi Defender for Identity. Użyj tego artykułu jako listy kontrolnej, aby upewnić się, że Twoje środowisko jest gotowe: Wymagania wstępne programu [Microsoft Defender dla tożsamości](/defender-for-identity/prerequisites).


## <a name="next-steps"></a>Następne kroki

Krok 2 z 3. Włączanie [środowiska oceny defender dla tożsamości](eval-defender-identity-enable-eval.md)

Wróć do przeglądu programu [Evaluate Microsoft Defender for Identity](eval-defender-identity-overview.md)

Wróć do przeglądu projektów [oceniania i Microsoft 365 Defender](eval-overview.md) 
