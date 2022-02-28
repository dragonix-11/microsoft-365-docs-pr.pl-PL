---
title: Monitorowanie zdarzeń dotyczących prywatności danych w organizacji i odpowiadanie na nie
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
description: Monitorowanie zdarzeń dotyczących danych osobowych i odpowiadanie na nie za pomocą zasad inspekcji i alertów oraz próśb osób, których dane dotyczą.
ms.openlocfilehash: 74efff60bb8e0ad6f170b57c86e384d3b689eee1
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988327"
---
# <a name="monitor-and-respond-to-data-privacy-incidents-in-your-organization"></a>Monitorowanie zdarzeń dotyczących prywatności danych w organizacji i odpowiadanie na nie

Microsoft 365 funkcje pomagają monitorować i badać zdarzenia związane z prywatnością danych w organizacji oraz reagować na nie w ramach operacyjnych funkcji pokrewnych. Posiadanie procesów, procedur i innej dokumentacji dla każdego z nich może być również ważne w celu zademonstrowania zgodności z przepisami przed organami regulacyjną.

Obejmują one: 

- Zasady inspekcji i alertów
- Żądania osób, których dane dotyczą (w tym przeszukiwanie zawartości i zbierania elektronicznych materiałów dowodowych)
- Dodatkowe narzędzia do badania i raportowanie

## <a name="data-privacy-regulations-impacting-the-use-of-monitoring-and-response-tools"></a>Przepisy dotyczące ochrony prywatności danych wpływające na korzystanie z narzędzi do monitorowania i reagowania

Oto przykładowy wykaz przepisów dotyczących ochrony prywatności danych, które mogą dotyczyć kontroli zarządzania informacjami:

- LGPD, artykuł 46
- LGPD, artykuł 48
- Artykuł RODO (5)(1)(f)
- Artykuł RODO (15)(1)(e)
- HIPAA-HITECH (45 C.F.R. 164.308(a)(1)(ii)(D))
- HIPAA-HITECH (45 C.F.R. 164.308(a)(6)(ii)
- HIPAA-HITECH (45 C.F.R. 164,312(b))
- RÓWNIEŻ (1798.105(c))

Aby uzyskać więcej informacji, zobacz [Ocenianie zagrożeń związanych z prywatnością danych i identyfikowanie informacji poufnych](information-protection-deploy-assess.md).

Przepisy dotyczące ochrony prywatności danych na ogół wywołują następujące zasady monitorowania i reagowania:

- Inspekcja, alertowanie i raportowanie działań związanych z przechowywaniem, udostępnianiem i przetwarzaniem danych osobowych
- Możliwość odpowiadania na żądanie podmiotu danych oraz, w niektórych przypadkach, wykonywania działań naprawczych i innych środków administracyjnych w celu spełnienia tych żądań.

Twoja organizacja może także chcieć wykonywać działania monitorujące i reagowanie w innych celach, takich jak potrzeby w zakresie zgodności z przepisami lub ze względów biznesowych. Ustanawianie schematu monitorowania i reakcji w zakresie ochrony prywatności danych należy stosować w ramach ogólnego planowania monitorowania i reagowania, wdrażania i zarządzania.

Aby ułatwić rozpoczynanie pracy ze schematem monitorowania i reagowania w programie Microsoft 365 ochrony prywatności danych, ten artykuł zawiera listę przydatnych funkcji w zakresie Microsoft 365 odpowiedzi na pytania takie jak: 

- Jakie rodzaje technik monitorowania, badania i raportowania są dostępne w przypadku różnych typów danych i źródeł?
- Jakie mechanizmy będą potrzebne do obsługi żądań osób, których dane dotyczą, i wszelkich działań naprawczych, takich jak anonimizacja, ponowne działanie i usuwanie.

## <a name="auditing-and-alert-policies-in-the-security-and-compliance-center"></a>Zasady inspekcji i alertów w Centrum zabezpieczeń i zgodności

Zobacz następujące artykuły dotyczące konfigurowania inspekcji, zaawansowanej inspekcji i zasad alertów:

- [Ujednolicona inspekcja](../compliance/search-the-audit-log-in-security-and-compliance.md)
- [Inspekcja skrzynki pocztowej](../compliance/enable-mailbox-auditing.md)
- [Zaawansowana inspekcja](../compliance/advanced-audit.md)
- [Zasady alertów](../compliance/alert-policies.md)

## <a name="data-subject-requests-for-the-gdpr-and-ccpa"></a>Wnioski osób, których dane dotyczą, w związku z RODO i ZESZYT

Zobacz [Żądania osób, których dane dotyczą, w związku z RODO i ZEA](/compliance/regulatory/gdpr-dsr-Office365), aby uzyskać informacje na temat odpowiadania na dane DSR w Microsoft 365.

## <a name="manage-deleted-users-in-microsoft-stream"></a>Zarządzanie usuniętymi użytkownikami w uwitrynie Microsoft Stream

W przypadku usługi Microsoft Stream po usunięciu użytkownika z usługi Azure Active Directory (Azure AD), jeśli jego nazwa była wcześniej skojarzona z opublikowanym klipem wideo usługi Stream, jego adres e-mail pozostaje skojarzony z klipem wideo. Zobacz [Zarządzanie usuniętymi użytkownikami z usługi Microsoft Stream](/stream/managing-deleted-users) , aby go usunąć.

## <a name="insider-risk-management-as-an-investigative-tool"></a>Zarządzanie ryzykiem niejawnego programu testów jako narzędzie do badania

[Zarządzanie ryzykiem](../compliance/insider-risk-management.md) niejawnego programu testów w programie Microsoft 365 to funkcja centrum administracyjnego zgodności firmy Microsoft ułatwiająca minimalizowanie ryzyka wewnętrznego przez wykrywanie, badanie i działanie w przypadku ryzykownych działań w organizacji.