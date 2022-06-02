---
title: Licencjonowanie usługi SharePoint Syntex
ms.author: mikeplum
author: MikePlumleyMSFT
ms.reviewer: ssquires
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
search.appverid: MET150
ms.localizationpriority: high
description: Dowiedz się więcej o licencjonowaniu SharePoint Syntex
ms.openlocfilehash: 7a7f310cb9c925fdb98a38ee12335abde91ea1db
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2022
ms.locfileid: "65839335"
---
# <a name="licensing-for-sharepoint-syntex"></a>Licencjonowanie usługi SharePoint Syntex

Aby korzystać z SharePoint Syntex, organizacja musi mieć subskrypcję do SharePoint Syntex, a każdy użytkownik SharePoint Syntex musi mieć licencję. Jeśli anulujesz subskrypcję SharePoint Syntex w przyszłości (lub wersja próbna wygaśnie), użytkownicy nie będą już mogli tworzyć, publikować ani uruchamiać modeli interpretacji dokumentów ani przetwarzania formularzy. Ponadto raporty magazynu terminów, import taksonomii SKOS i wypychanie typu zawartości nie będą już dostępne. Żadne modele, zawartość ani metadane nie zostaną usunięte, a uprawnienia witryny nie zostaną zmienione.
 
> [!NOTE] 
> SharePoint Syntex jest licencją dodatkową i wymaga od użytkowników posiadania licencji na Microsoft 365.
 
## <a name="tasks-requiring-a-license"></a>Zadania wymagające licencji
 
Następujące zadania wymagają [licencji SharePoint Syntex](https://www.microsoft.com/microsoft-365/enterprise/sharepoint-syntex) dla użytkownika, który je wykonuje:
 
- Stosowanie modelu zrozumienia dokumentu do biblioteki. (Nielicencjonowani użytkownicy mogą mieć dostęp do centrum zawartości i mogą tworzyć modele interpretacji dokumentów, ale nie mogą ich stosować do biblioteki dokumentów).
- Tworzenie modelu przetwarzania formularzy za pośrednictwem punktu wejścia w bibliotece
- Przekazywanie zawartości do biblioteki, w której zastosowano model interpretacji dokumentów lub przetwarzania formularzy
- Uruchamianie modelu zrozumienia dokumentu na żądanie
- Korzystanie z usług taksonomii premium. (Premium usługi taksonomii obejmują importowanie zestawów terminów opartych na systemie SKOS, wypychanie typów zawartości przedsiębiorstwa do witryn skojarzonych z centrum i raporty magazynu terminów).

Nielicencjonowanym użytkownikom można udzielić dostępu do centrum zawartości i tworzyć modele interpretacji dokumentów, ale nie mogą ich stosować do biblioteki dokumentów.
 
## <a name="cost-of-training-and-running-models"></a>Koszt trenowania i uruchamiania modeli
 
Koszt trenowania i uruchamiania modeli zrozumienia dokumentów jest uwzględniany w kosztach licencji SharePoint Syntex. Jednak modele przetwarzania formularzy używają pojemności narzędzia AI Builder zarówno do trenowania, jak i przetwarzania w czasie wykonywania. Pojemność musi zostać przydzielona do środowiska Power Apps, w którym będziesz używać narzędzia AI Builder.

Dla każdego SharePoint Syntex licencji przydzielono 3500 środków na narzędzie AI Builder na licencję miesięcznie w puli na poziomie dzierżawy z maksymalną alokacją 1 miliona środków miesięcznie. Ta alokacja jest odnawiana co miesiąc dla każdej aktywnej licencji SharePoint Syntex. (Nieużywane środki nie są przenoszone z miesiąca na miesiąc). 

Możesz oszacować pojemność narzędzia AI Builder, która jest odpowiednia dla Ciebie, za pomocą [kalkulatora narzędzia AI Builder](https://powerapps.microsoft.com/ai-builder-calculator).

Jeśli planujesz korzystanie z niestandardowego środowiska platformy Power Platform, musisz [przydzielić środki do tego środowiska](/power-platform/admin/capacity-add-on).

Przejdź do [centrum administracyjnego platformy Power Platform](https://admin.powerplatform.microsoft.com/resources/capacity) , aby sprawdzić środki i użycie.
  
## <a name="additional-term-store-features"></a>Dodatkowe funkcje magazynu terminów
 
Subskrypcja SharePoint Syntex oferuje następujące dodatkowe funkcje magazynu terminów:
 
- Importowanie zestawu terminów opartego na systemie SKOS
- Wypychanie typów zawartości przedsiębiorstwa do lokacji centrum, która dodaje je również do skojarzonych witryn i wszystkich nowo utworzonych list lub bibliotek
- Raporty magazynu terminów zapewniające wgląd w opublikowane zestawy terminów i ich użycie w całej dzierżawie


## <a name="see-also"></a>Zobacz też

[Omówienie licencjonowania dla platformy Microsoft Power Platform](/power-platform/admin/pricing-billing-skus)

[często zadawane pytania dotyczące licencjonowania Power Apps i Power Automate](/power-platform/admin/powerapps-flow-licensing-faq)
