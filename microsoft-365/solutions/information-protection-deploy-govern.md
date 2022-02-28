---
title: Reguluj informacje objęte rozporządzeniem o ochronie prywatności danych
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
description: Etykiety Microsoft 365 zasady i etykiety przechowywania można używać do zarządzania danymi osobistymi w środowisku Microsoft 365 danych.
ms.openlocfilehash: b131c90e83a2ce211d51af444dd570f71f3b8263
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984368"
---
# <a name="govern-information-subject-to-data-privacy-regulation"></a>Reguluj informacje objęte rozporządzeniem o ochronie prywatności danych

Mechanizmy kontroli zarządzania informacjami można stosować w danym środowisku w celu spełniania wymagań dotyczących zachowania zgodności z przepisami dotyczącymi prywatności danych, w tym liczby specyficznej dla Ogólnego Rozporządzenia o Ochronie Danych (RODO), HIPAA-HITECH (united States health care privacy act), California Consumer Protection Act (INTERNETEMA) i brazylijskiej ustawy o ochronie danych (LGPD). 

Kontrolki te są przede wszystkim podzielone na następujące obszary rozwiązania:

- Zasady przechowywania
- Etykiety przechowywania
- Zarządzanie rekordami

## <a name="data-privacy-regulations-impacting-information-governance-controls"></a>Przepisy dotyczące ochrony prywatności danych wpływające na mechanizmy kontroli zarządzania informacjami

Oto przykładowy wykaz przepisów dotyczących ochrony prywatności danych, które mogą dotyczyć kontroli zarządzania informacjami:

- Artykuł RODO (13)(2)(a)
- Artykuł RODO (5)(1)(f)
- HIPAA-HITECH (45 CFR 164.312(c)(2))
- HIPAA-HITECH (45 CFR 164.316(b)(1)(i))
- HIPAA-HITECH (45 CFR 164.316(b)(1)(ii))
- LGPD, artykuł 46

Aby uzyskać więcej informacji na temat tych przepisów, zobacz artykuł Ocenianie ryzyka związanego z prywatnością danych [i identyfikowanie informacji poufnych](information-protection-deploy-assess.md).

W przypadku zarządzania informacjami przepisy dotyczące prywatności danych najczęściej wymagają następujących czynności:

- Należy stosować schemat techniczny przechowywania i usuwania danych osobowych przechowywanych w Microsoft 365.
- Jeśli zamierzasz przechowywać dane osobowe, poinformuj o tym, jak długo dane będą przechowywane, co jest standardową praktyką w front-end systemach sieci Web.
- Dane osobowe powinny być chronione przed przypadkowym przetwarzaniem, utratą lub zmianą przy użyciu weryfikowalnych metod.
- Wszelkie działania wykonywane na danych osobowych należy udokumentować, a ta dokumentacja powinna być zachowana przez określony czas.

Ze względu na to, że przepisy dotyczące prywatności danych nie są zbyt szczegółowe w zakresie przechowywania i usuwania danych, należy wziąć pod uwagę inne czynniki, które mogą określać wytyczne dotyczące zarządzania informacjami dotyczącymi informacji osobistych przechowywanych w subskrypcji usługi Microsoft 365 firm. Oto kilka przykładów:

- Starzeją się konta klientów po 5 latach nieaktywności i wymagają usunięcia lub anonimizacji danych konta po tym punkcie, co wymaga ujednania między systemem przechowywania danych i przepływów pracy związanych z powiadomieniami i inną automatyzacją.
- Konfigurowanie reguł i procedur dotyczących RODO przez trzy lata po ich przesłoniu, co jest zgodne z harmonogramem przechowywania zasad i procedur obowiązujących w organizacji.
- Utrzymywanie osobnej subskrypcji na rzecz komunikowania się z użytkownikami za pośrednictwem organizacji pomocy technicznej. Cała komunikacja za pomocą poczty e-mail została zachowana i usunięta po dwóch tygodniach, aby ograniczyć liczbę kompilacji dotyczących prywatności w systemie.

Kluczowe pytanie, na które należy odpowiedzieć, to: 

- Jak długo informacje zawierające dane osobowe muszą być przechowywane w prawidłowych celach biznesowych, aby uniknąć praktyk "zachowaj to na zawsze"? Musi to być równoważyć się potrzebami przechowywania, aby zapewnić ciągłość działania tej firmy.

Niezależnie od celów prawnych i biznesowych przechowywania informacji osobistych lub ich usuwania firma Microsoft udostępnia szereg możliwości implementowania schematu zarządzania danymi w Microsoft 365.

## <a name="managing-information-governance-in-microsoft-365"></a>Zarządzanie zarządzaniem informacjami w Microsoft 365

Aby rozpocząć, zobacz [Zarządzanie informacjami oraz](../compliance/manage-information-governance.md) [Przechowywanie, usuwanie i schowek danych w Microsoft 365](/office365/Enterprise/office-365-data-retention-deletion-and-destruction-overview).

### <a name="develop-data-retention-schedules-for-containers-email-and-content"></a>Tworzenie harmonogramów przechowywania danych dla kontenerów, wiadomości e-mail i zawartości

Należy pamiętać o następujących kwestiach:

- Ustanowienie harmonogramu przechowywania danych dla zdefiniowanych typów informacji powinno być traktowane jako wymaganie wstępne w celu wdrożenia dowolnego schematu przechowywania lub usuwania.

- Biorąc pod uwagę liczbę typów informacji, które większość organizacji uznaje za ważne, oraz odpowiadające im harmonogramy przechowywania dużych rekordów, które się z nimi do nich do sobą do nich dochodają, wdrożenie strategii przechowywania danych i zarządzania rekordami wymaga planowania. 

- Kluczem do ustanawiania skutecznej strategii zarządzania danymi tego typu jest skoncentrowanie się na funkcjach biznesowych o najwyższym priorytecie i typach informacji wymagających bardziej formalnego zarządzania. Przykłady to umowy prawne, wyciągi finansowe i dokumentacja dotycząca zgodności z przepisami. Unikaj stosowania oddzielnego harmonogramu przechowywania dla każdego typu informacji. Próbuj korzystać z kategorii ogólnych w jak naj jak najbardziej ogólnym poziomie, na przykład z harmonogramami przechowywania 7 lat dla ogólnej zawartości biznesowej.

- Gdy typy informacji osobistych w środowisku będą lepiej znane, ustal harmonogramy przechowywania i usuwania dla tego typu zawartości i dostosuj architekturę informacji, aby ułatwić zarządzanie tego rodzaju informacjami. Na przykład wyodrębnij informacje osobiste w osobnych witrynach, bibliotekach lub folderach z kontrolowanym dostępem.

### <a name="retention-policies-and-retention-labels"></a>Zasady przechowywania i etykiety przechowywania

Zasady [przechowywania i etykiety przechowywania](../compliance/retention.md) zachowują lub usuwaj zawartość w Microsoft 365, która zawiera dane osobowe lub powinna ich zawierać.

### <a name="records-management"></a>Zarządzanie rekordami

Skorzystaj z etykiet przechowywania, które deklarują zawartość rekordu, aby zaimplementować rozwiązanie [do](../compliance/records-management.md) zarządzania rekordami dla danych w Microsoft 365.

W przypadku ochrony prywatności danych wnioski osób, których dane dotyczą, są deklarowane przez dział prawny jako rekord i mogą być przechowywane bezterminowo lub usunięte wraz z dowód w celu zachowania zgodności ze specyfikacjami przechowywania dotyczącymi działań prawnych.