---
title: Zarządzanie informacjami podlegającymi przepisom dotyczącym prywatności danych
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 06/09/2020
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
description: Użyj Microsoft 365 etykiet przechowywania i zasad, aby zarządzać danymi osobowymi w środowisku Microsoft 365.
ms.openlocfilehash: 05aad5b26f65dc66543afb29834e7cc4514e3366
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64947390"
---
# <a name="govern-information-subject-to-data-privacy-regulation"></a>Zarządzanie informacjami podlegającymi przepisom dotyczącym prywatności danych

Mechanizmy kontroli ładu informacji mogą być stosowane w twoim środowisku, aby pomóc spełnić wymagania dotyczące zgodności z prywatnością danych, w tym liczbę specyficzną dla ogólnych przepisów o ochronie danych (RODO), HIPAA-HITECH (Stany Zjednoczone ustawy o ochronie prywatności w służbie zdrowia), ustawy o ochronie konsumentów w Kalifornii (CCPA) i brazylijskiej ustawy o ochronie danych (LGPD). 

Te kontrolki należą przede wszystkim do następujących obszarów rozwiązania:

- Zasady przechowywania
- Etykiety przechowywania
- Zarządzanie rekordami

## <a name="data-privacy-regulations-impacting-information-governance-controls"></a>Przepisy dotyczące prywatności danych wpływające na mechanizmy kontroli ładu informacji

Oto przykładowa lista przepisów dotyczących prywatności danych, które mogą odnosić się do mechanizmów kontroli ładu informacji:

- RODO , art.
- RODO , art.
- HIPAA-HITECH (45 CFR 164.312(c)(2))
- HIPAA-HITECH (45 CFR 164.316(b)(1)(i))
- HIPAA-HITECH (45 CFR 164.316(b)(1)(ii))
- ARTYKUŁ LGPD 46

Aby uzyskać więcej informacji na temat tych przepisów, zobacz [artykuł Dotyczący oceny ryzyka związanego z prywatnością danych i identyfikowania informacji poufnych](information-protection-deploy-assess.md).

W przypadku ładu informacyjnego przepisy dotyczące prywatności danych zwykle wymagają następujących czynności:

- Należy zastosować system techniczny do przechowywania i usuwania danych osobowych przechowywanych w Microsoft 365.
- Jeśli zamierzasz przechowywać dane osobowe, poinformuj podmiot o tym, jak długo będą przechowywane dane, co jest obecnie standardową praktyką w systemach internetowych frontonu.
- Dane osobowe powinny być chronione przed przypadkowym przetwarzaniem, utratą lub zmianą przy użyciu weryfikowalnych metod.
- Wszelkie działania wykonywane względem danych osobowych powinny być udokumentowane, a dokumentacja powinna być przechowywana przez określony czas.

Ponieważ przepisy dotyczące prywatności danych nie są bardzo specyficzne, jeśli chodzi o przechowywanie i usuwanie danych, należy wziąć pod uwagę inne czynniki, które mogą dyktować wytyczne dotyczące ładu informacji dla danych osobowych przechowywanych w subskrypcji Microsoft 365. Oto kilka przykładów:

- Starzenie się kont konsumentów po 5 latach braku aktywności i wymaga usunięcia lub zanonimizowania danych konta po tym punkcie, co wymaga orkiestracji między systemem przechowującym dane i przepływy pracy związane z powiadomieniami i inną automatyzacją.
- Konfigurowanie reguł przechowywania zasad i procedur związanych z RODO przez trzy lata po ich zastąpieniu, co jest zgodne z harmonogramem przechowywania zasad i procedur organizacji.
- Utrzymywanie oddzielnej subskrypcji do komunikowania się z konsumentami za pośrednictwem organizacji pomocy technicznej. Wszystkie wiadomości e-mail zostały zachowane i usunięte po dwóch tygodniach, aby zmniejszyć wszelkie narastanie zadłużenia prywatności w systemie.

Kluczowe pytanie, na które należy odpowiedzieć, to: 

- Jak długo należy przechowywać informacje zawierające dane osobowe z ważnych powodów biznesowych, aby uniknąć praktyk "utrzymywania ich na zawsze"? Musi to być zrównoważone z potrzebami przechowywania w celu zapewnienia ciągłości działania.

Niezależnie od przyczyn prawnych i biznesowych związanych z przechowywaniem danych osobowych lub ich usuwaniem, firma Microsoft oferuje szereg możliwości wdrażania schematu ładu danych w Microsoft 365.

## <a name="managing-information-governance-in-microsoft-365"></a>Zarządzanie zarządzaniem zarządzaniem informacjami w Microsoft 365

Aby rozpocząć, zobacz [Zarządzanie danymi za pomocą usługi Microsoft Purview](../compliance/manage-data-governance.md) i [przechowywania danych, usuwania i niszczenia w Microsoft 365](/office365/Enterprise/office-365-data-retention-deletion-and-destruction-overview).

### <a name="develop-data-retention-schedules-for-containers-email-and-content"></a>Opracowywanie harmonogramów przechowywania danych dla kontenerów, poczty e-mail i zawartości

Należy pamiętać o następujących kwestiach:

- Ustanowienie harmonogramu przechowywania danych dla zdefiniowanych typów informacji należy uznać za warunek wstępny wdrożenia jakiegokolwiek schematu przechowywania lub usuwania.

- Biorąc pod uwagę liczbę typów informacji, które większość organizacji uważa za ważne, oraz odpowiednie harmonogramy przechowywania dużych rekordów, które wraz z nimi istnieją, wdrożenie strategii zarządzania przechowywaniem danych i rekordami wymaga planowania. 

- Kluczem do ustanowienia skutecznej strategii zarządzania danymi tego typu jest skupienie się na funkcjach biznesowych o najwyższym priorytecie i typach informacji, które wymagają bardziej formalnego zarządzania. Przykłady to kontrakty prawne, sprawozdania finansowe i dokumentacja zgodności z przepisami. Staraj się unikać posiadania oddzielnego harmonogramu przechowywania dla każdego typu informacji. Spróbuj jak najwięcej wykorzystać kategorie ogólne, na przykład z harmonogramami przechowywania wynoszącymi 7 lat dla ogólnej zawartości biznesowej.

- Gdy typy danych osobowych w twoim środowisku będą lepiej znane, ustal harmonogramy przechowywania i usuwania tego typu zawartości oraz dostosuj architekturę informacji, aby ułatwić zarządzanie tego rodzaju informacjami. Na przykład wyizoluj dane osobowe w oddzielnych witrynach, bibliotekach lub folderach z kontrolowanym dostępem.

### <a name="retention-policies-and-retention-labels"></a>Zasady przechowywania i etykiety przechowywania

Użyj [zasad przechowywania i etykiet przechowywania](../compliance/retention.md), aby zachować lub usunąć zawartość w Microsoft 365, która zawiera lub ma zawierać dane osobowe.

### <a name="records-management"></a>Zarządzanie rekordami

Użyj etykiet przechowywania, które deklarują zawartość jako rekord, aby zaimplementować [rozwiązanie do zarządzania rekordami](../compliance/records-management.md) dla danych w Microsoft 365.

W przypadku ochrony prywatności danych żądania podmiotów danych otrzymane przez dział prawny są deklarowane jako rekordy i mogą być przechowywane na czas nieokreślony lub usuwane z dowodem, aby przestrzegać specyfikacji przechowywania działań regulacyjnych.