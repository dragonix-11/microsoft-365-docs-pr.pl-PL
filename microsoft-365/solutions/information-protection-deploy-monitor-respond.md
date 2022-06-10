---
title: Monitorowanie i reagowanie na zdarzenia związane z prywatnością danych w organizacji
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 01/04/2021
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
ms.custom: ''
description: Użyj zasad inspekcji i alertów oraz żądań podmiotów danych, aby monitorować zdarzenia dotyczące danych osobowych i reagować na nie.
ms.openlocfilehash: 5954fc193f6071dbf94277ff57f599e3bb98f7d2
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66013271"
---
# <a name="monitor-and-respond-to-data-privacy-incidents-in-your-organization"></a>Monitorowanie i reagowanie na zdarzenia związane z prywatnością danych w organizacji

Microsoft 365 funkcje ułatwiają monitorowanie, badanie i reagowanie na zdarzenia związane z prywatnością danych w organizacji podczas operacji związanych z nimi możliwości. Posiadanie procesów, procedur i innej dokumentacji dla każdego z nich może być również ważne, aby zademonstrować zgodność z organami regulacyjnymi.

Obejmują one: 

- Zasady inspekcji i alertów
- Żądania podmiotów danych (w tym wyszukiwanie zawartości i zbieranie elektronicznych materiałów dowodowych)
- Dodatkowe narzędzia śledcze i raportowanie

## <a name="data-privacy-regulations-impacting-the-use-of-monitoring-and-response-tools"></a>Przepisy dotyczące prywatności danych wpływające na korzystanie z narzędzi do monitorowania i reagowania

Oto przykładowa lista przepisów dotyczących prywatności danych, które mogą odnosić się do mechanizmów kontroli ładu informacji:

- ARTYKUŁ LGPD 46
- Artykuł 48 LGPD
- RODO , art.
- RODO , art.
- HIPAA-HITECH (45 C.F.R. 164.308(a)(1)(ii)(D))
- HIPAA-HITECH (45 C.F.R. 164.308(a)(6)(ii)
- HIPAA-HITECH (45 C.F.R. 164.312(b))
- CCPA (1798.105(c))

Aby uzyskać więcej informacji, zobacz [Ocena ryzyka związanego z prywatnością danych i identyfikowanie informacji poufnych](information-protection-deploy-assess.md).

Przepisy dotyczące prywatności danych zwykle wymagają następujących celów monitorowania i reagowania:

- Inspekcja, alerty i raportowanie działań związanych z przechowywaniem, udostępnianiem i przetwarzaniem danych osobowych
- Możliwość reagowania na żądanie podmiotu danych (DSR), a w niektórych przypadkach wykonywania czynności dochodzeniowych i innych środków administracyjnych w celu spełnienia takich żądań.

Organizacja może również chcieć wykonywać działania monitorowania i reagowania na nie do innych celów, takich jak inne potrzeby w zakresie zgodności lub ze względów biznesowych. Ustanowienie schematu monitorowania i reagowania na prywatność danych powinno odbywać się w ramach ogólnego planowania monitorowania i reagowania, wdrażania i zarządzania nimi.

Aby ułatwić rozpoczęcie pracy ze schematem monitorowania i reagowania w Microsoft 365 dla przepisów dotyczących prywatności danych, w tym artykule wymieniono przydatne funkcje w Microsoft 365 odpowiedzi na pytania, takie jak: 

- Jakiego rodzaju codzienne techniki monitorowania, analizy i raportowania są dostępne dla różnych typów danych i źródeł?
- Jakie mechanizmy będą potrzebne do obsługi żądań podmiotów danych (DSR) i wszelkich akcji korygowania, takich jak anonimizacja, ponowna akcja i usuwanie.

## <a name="auditing-and-alert-policies-in-the-microsoft-purview-compliance-portal"></a>Zasady inspekcji i alertów w portalu zgodności usługi Microsoft Purview

Zobacz następujące artykuły dotyczące konfigurowania zasad inspekcji, zaawansowanej inspekcji i alertów:

- [Ujednolicona inspekcja](../compliance/search-the-audit-log-in-security-and-compliance.md)
- [Inspekcja skrzynki pocztowej](../compliance/enable-mailbox-auditing.md)
- [Inspekcja (wersja Premium)](../compliance/advanced-audit.md)
- [Zasady alertów](../compliance/alert-policies.md)

## <a name="data-subject-requests-for-the-gdpr-and-ccpa"></a>Żądania podmiotów danych dotyczące RODO i CCPA

Aby uzyskać informacje na temat reagowania na DSR w Microsoft 365, zobacz [Żądania podmiotów danych dotyczące RODO i CCPA](/compliance/regulatory/gdpr-dsr-Office365).

## <a name="manage-deleted-users-in-microsoft-stream"></a>Zarządzanie usuniętymi użytkownikami w Microsoft Stream

W przypadku Microsoft Stream, gdy użytkownik zostanie usunięty z Azure Active Directory (Azure AD), jeśli jego nazwa została skojarzona z opublikowanym filmem wideo usługi Stream przed tym punktem, jego adres e-mail pozostaje skojarzony z filmem wideo. Zobacz [Zarządzanie usuniętymi użytkownikami z Microsoft Stream](/stream/managing-deleted-users), aby go usunąć.

## <a name="insider-risk-management-as-an-investigative-tool"></a>Zarządzanie ryzykiem wewnętrznym jako narzędzie śledcze

[Zarządzanie ryzykiem wewnętrznym](../compliance/insider-risk-management.md) to funkcja portalu zgodności usługi Microsoft Purview, która pomaga zminimalizować ryzyko wewnętrzne, umożliwiając wykrywanie, badanie i podjęcie działań dotyczących ryzykownych działań w organizacji.
