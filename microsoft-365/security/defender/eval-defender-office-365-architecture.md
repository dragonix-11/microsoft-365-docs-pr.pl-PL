---
title: Zapoznaj się z wymaganiami architektury i pojęciami planowania dla programu Microsoft Defender dla Office 365
description: Diagram techniczny programu Microsoft Defender Office 365 w programie Microsoft 365 Defender pomaga zrozumieć tożsamość w programie Microsoft 365 przed rozpoczęciem tworzenia laboratorium próbnego lub środowiska pilotażowego.
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
ms.date: 07/01/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 49acb346be872c870f1ae52024963680e6631363
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010386"
---
# <a name="review-microsoft-defender-for-office-365-architecture-requirements-and-key-concepts"></a>Zapoznaj się z programem Microsoft Defender Office 365 kluczowych pojęć związanych z architekturą i


**Dotyczy:**
- Microsoft 365 Defender

Ten artykuł dotyczy [kroku 1 z 3](eval-defender-office-365-overview.md) w procesie konfigurowania środowiska oceny dla programu Microsoft Defender dla systemu Office 365. Aby uzyskać więcej informacji na temat tego procesu, zobacz artykuł [z omówieniem](eval-defender-office-365-overview.md).

Przed włączeniem usługi Defender Office 365 upewnij się, że rozumiesz architekturę i może spełniać wymagania. W tym artykule opisano architekturę, kluczowe pojęcia i wymagania wstępne, które musi spełnić Exchange Online środowisko użytkownika.

## <a name="understand-the-architecture"></a>Opis architektury

Na poniższym diagramie przedstawiono architekturę podstawową programu Microsoft Defender Office dla systemu Office, która może obejmować bramę SMTP innej firmy lub integrację lokalną. Scenariusze współistnienia hybrydowego (czyli produkcyjne skrzynki pocztowe są zarówno lokalne, jak i online) wymagają bardziej złożonych konfiguracji i nie są uwzględnione w tym artykule ani wskazówkach dotyczących oceny.

![Architektura programu Microsoft Defender dla Office 365.](../../media/defender/m365-defender-office-architecture.png)

W poniższej tabeli opisano tę ilustrację.

|Call-out  |Opis  |
|---------|---------|
|1     | Serwer hosta nadawcy zewnętrznego zwykle wykonuje publiczne odnośniki DNS dla rekordu MX, który zapewnia serwer docelowy do przekazywania wiadomości.  To odwołanie można skonfigurować Exchange Online (EXO) lub bramy SMTP, która została skonfigurowana do przekazywania dla serwera EXO.  |
|2     | Exchange Online Protection podczas negocjacji i weryfikacji połączenia przychodzącego oraz przeprowadza inspekcję nagłówków wiadomości i zawartości w celu określenia, jakie dodatkowe zasady, otagowanie lub przetwarzanie są wymagane.  |
|3     | Exchange Online program Microsoft Defender na Office 365 oferuje bardziej zaawansowaną ochronę przed zagrożeniami, środki zaradcze i środki zaradcze. |
|4     | Wiadomość, która nie jest złośliwa, zablokowana lub poddana kwarantannie, jest przetwarzana i dostarczana do adresata w we wyzwolony sposób, w którym preferencje użytkownika dotyczące wiadomości-śmieci, reguł skrzynki pocztowej lub innych ustawień są sprawdzane i wyzwalane. |
|5     | Integrację z lokalną usługą Active Directory można włączyć przy użyciu usługi Azure AD Połączenie w celu synchronizowania i inicjowania obsługi obiektów i kont z obsługą poczty w celu Azure Active Directory i ostatecznie Exchange Online. |
|6     | Podczas integrowania środowiska lokalnego zdecydowanie zaleca się używanie serwera poczty Exchange do obsługiwanego zarządzania atrybutami, ustawieniami i konfiguracjami związanych z pocztą oraz administrowania nimi |
|7     | Usługa Microsoft Defender for Office 365 udostępnia sygnały do Microsoft 365 Defender wykrywania rozszerzonego i odpowiedzi (XDR).|

Integracja lokalna jest wspólna, ale opcjonalna. Jeśli Twoje środowisko działa tylko w chmurze, te wskazówki również będą dla Ciebie.

## <a name="understand-key-concepts"></a>Opis kluczowych pojęć

W poniższej tabeli przedstawiono kluczowe pojęcia, które należy zrozumieć podczas oceniania, konfigurowania i wdrażania aplikacji MDO.


|Pojęcie  |Opis |Więcej informacji  |
|---------|---------|---------|
|Exchange Online Protection      |    Exchange Online Protection (EOP) to oparta na chmurze usługa filtrowania, która pomaga chronić twoją organizację przed wiadomościami e-mail ze spamem i złośliwym oprogramowaniem. Program EOP jest uwzględniony we wszystkich Microsoft 365, które zawierają Exchange Online.     |   [Exchange Online Protection omówienie](../office-365-security/exchange-online-protection-overview.md)      |
|Ochrona przed złośliwym oprogramowaniem     |    Organizacje ze skrzynkami pocztowymi w exo są automatycznie chronione przed złośliwym oprogramowaniem.     |  [Ochrona przed złośliwym oprogramowaniem w uchcie EOP](../office-365-security/anti-malware-protection.md)       |
|Ochrona przed spamem     |   Organizacje ze skrzynkami pocztowymi w exo są automatycznie chronione przed wiadomościami-śmieciami i zasadami spamu.      |  [Ochrona przed spamem w uciekaniu poczty eop](../office-365-security/anti-spam-protection.md)       |
|Ochrona przed wyłudzaniem informacji |  MDO oferuje bardziej zaawansowaną ochronę przed wyłudzaniem informacji związaną z wyłudzaniem informacji, wyłudzaniem informacji, oprogramowaniem wymuszającym okup i innymi złośliwymi działaniami.   | [Dodatkowa ochrona przed wyłudzaniem informacji w programie Microsoft Defender dla Office 365](../office-365-security/anti-phishing-protection.md)   |
|Ochrona przed fałszerami     |   Program EOP zawiera funkcje chroniące organizację przed fałszywymi (sfałszowanych) nadawcami.      |   [Ochrona przed fałszeringem w uciekaniu poczty eop](../office-365-security/anti-spoofing-protection.md)      |
|Sejf załączników     |   Sejf załączników zapewnia dodatkową warstwę ochrony za pomocą środowiska wirtualnego do sprawdzania i "detonacji" załączników w wiadomościach e-mail przed ich dostarczeniaą.      |   [Sejf załączników w programie Microsoft Defender dla Office 365](../office-365-security/safe-attachments.md)      |
|Sejf załączników do SharePoint, OneDrive i Microsoft Teams     |    Ponadto załączniki Sejf dla SharePoint, OneDrive i Microsoft Teams oferują dodatkową warstwę ochrony plików, które zostały przekazane do repozytoriów magazynu w chmurze.     |  [Sejf załączników do SharePoint, OneDrive i Microsoft Teams](../office-365-security/mdo-for-spo-odb-and-teams.md)       |
|Bezpieczne linki     | Sejf linków to funkcja, która umożliwia skanowanie i ponowne wysyłanie adresów URL w przychodzących wiadomościach e-mail oraz oferuje weryfikację tych linków przed ich dostarczenia lub kliknięciami.        |   [Sejf linków w programie Microsoft Defender dla Office 365](../office-365-security/safe-links.md)      |
|    |         |         |

Aby uzyskać bardziej szczegółowe informacje o możliwościach programu Microsoft Defender dla systemu Office, zobacz [Program Microsoft Defender, Office 365 opis usługi](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description).

## <a name="review-architecture-requirements"></a>Przejrzyj wymagania dotyczące architektury
Pomyślnie ocenianie mDO lub projekt pilotażowy produkcji zakłada następujące wymagania wstępne:
- Wszystkie skrzynki pocztowe adresatów znajdują się obecnie w Exchange Online.
- Publiczny rekord MX jest rozsyłany bezpośrednio do usługi EOP lub innej bramy SMTP, która następnie przekazuje przychodzące zewnętrzne wiadomości e-mail bezpośrednio do usługi EOP.
- Podstawowa domena poczty e-mail jest konfigurowana jako *autorytatywny w* Exchange Online.
- Pomyślnie wdrożono i skonfigurowano blokowanie brzegowe oparte na *katalogu (* DBEB) zgodnie z potrzebami. Aby uzyskać więcej informacji, zobacz [Odrzucanie wiadomości Directory-Based adresatów](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking) przy użyciu blokowania krawędzi krawędzi.

> [!IMPORTANT]
> Jeśli te wymagania nie mają zastosowania lub nadal istnieje scenariusz współistnienia hybrydowego, usługa Microsoft Defender do oceny Office 365 może wymagać bardziej złożonych lub zaawansowanych konfiguracji, które nie są w pełni objęte tymi wskazówkami.

## <a name="siem-integration"></a>Integracja usług SIEM

Możesz zintegrować usługę Microsoft Defender for Office 365 z programem Microsoft Sentinel, aby w pełni analizować zdarzenia dotyczące zabezpieczeń w całej organizacji i tworzyć podręczniki w celu skutecznego i natychmiastowego reagowania. Aby uzyskać więcej informacji, zobacz [Połączenie z programu Microsoft Defender dla Office 365](/azure/sentinel/connect-office-365-advanced-threat-protection).

Program Microsoft Defender for Office 365 można również zintegrować z innymi rozwiązaniami do zarządzania informacjami o zabezpieczeniach i zdarzeniami przy użyciu interfejsu [API Office 365 Zarządzanie aktywnością](/office/office-365-management-api/office-365-management-activity-api-reference).

## <a name="next-steps"></a>Następne kroki

Krok 2 z 3. Włączanie [środowiska oceny Program Microsoft Defender dla programu Office 365](eval-defender-office-365-enable-eval.md)

Wróć do przeglądu [szacowania programu Microsoft Defender dla programu Office 365](eval-defender-office-365-overview.md)

Wróć do przeglądu projektów [oceniania i Microsoft 365 Defender](eval-overview.md) 
