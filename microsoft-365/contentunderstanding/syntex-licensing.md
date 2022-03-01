---
title: Licencjonowanie oprogramowania SharePoint Syntex
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
description: Dowiedz się więcej o licencjonowaniu usług SharePoint Syntex
ms.openlocfilehash: 497952498e3ead2166f7cda11f050d929e6b6b9c
ms.sourcegitcommit: dbce0b6e74ae2efec42fe2b3b82c8e8cabe0ddbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2022
ms.locfileid: "63015795"
---
# <a name="licensing-for-sharepoint-syntex"></a>Licencjonowanie oprogramowania SharePoint Syntex

Aby można było SharePoint Syntex, organizacja musi mieć subskrypcję usługi SharePoint Syntex, a każdy użytkownik obiektu Syntex musi mieć licencję. Jeśli subskrypcja usługi SharePoint Syntex zostanie anulowana w przyszłości (lub wygaśnie), użytkownicy nie będą już mogli tworzyć, publikować ani uruchamiać modeli przetwarzania formularzy ani zrozumienia dokumentów. Ponadto nie będą już dostępne raporty magazynu okresów, importowanie taksonomii SKOS i wypychanie typu zawartości. Nie zostaną usunięte żadne modele, zawartość ani metadane i uprawnienia witryny nie zostaną zmienione.
 
> [!NOTE] 
> SharePoint Syntex jest licencją dodatkową i wymaga, aby użytkownicy mieli również licencję na Microsoft 365.
 
## <a name="tasks-requiring-a-license"></a>Zadania wymagające licencji
 
Następujące zadania wymagają licencji [SharePoint Syntex](https://www.microsoft.com/microsoft-365/enterprise/sharepoint-syntex) użytkownika wykonującego te zadania:
 
- Stosowanie modelu rozumienia dokumentu do biblioteki. (Nielicencjonowani użytkownicy mogą mieć przyznany dostęp do centrum zawartości i mogą tam tworzyć modele opisowe dokumentów, ale nie mogą stosować ich do biblioteki dokumentów).
- Tworzenie modelu przetwarzania formularza za pośrednictwem punktu wejścia w bibliotece
- Przekazywanie zawartości do biblioteki, w której zastosowano opis dokumentu lub model przetwarzania formularza
- Uruchamianie dokumentu opisz model na żądanie
- Korzystanie z usług taksonomii premium. (Premium usług taksonomii obejmuje importowanie zestawu terminów oparte na systemie SKOS, wypychanie typów zawartości przedsiębiorstwa do witryn skojarzonych ze centrum oraz raportów magazynu terminów.

Nielicencjonowani użytkownicy mogą mieć przyznany dostęp do centrum zawartości i mogą tam tworzyć modele opisowe dokumentów, ale nie mogą stosować ich do biblioteki dokumentów.
 
## <a name="cost-of-running-models"></a>Koszt działających modeli
 
Koszt pracy nad modelami zrozumienia dokumentów jest uwzględniony w kosztach licencji SharePoint Syntex dokumentów. Modele przetwarzania formularzy używają jednak pojemności konstruktora AI, zarówno do przetwarzania szkoleń, jak i środowiska uruchomieniowego. Pojemność musi zostać przydzielona do środowiska Power Apps, w którym będzie korzystać z aplikacji AI Builder.
 
Jeśli masz co najmniej 300 SharePoint Syntex licencji na SharePoint Syntex w organizacji, zostanie Ci przydzielony milion środków w aplikacji AI Builder. Ta pojemność jest odnawiana co miesiąc, jeśli zostanie zachowana wartość co najmniej 300 licencji. (Niewykorzystane środki nie są rzutowane z miesiąca na miesiąc). Jeśli masz mniej niż 300 licencji, musisz zakupić środki aplikacji AI Builder, aby korzystać z przetwarzania formularzy.
 
Można oszacować odpowiednią pojemność aplikacji AI Builder za pomocą [kalkulatora aplikacji AI Builder](https://powerapps.microsoft.com/ai-builder-calculator).

Jeśli planujesz korzystać z niestandardowego środowiska platformy Power Platform, musisz [przydzielić środki do tego środowiska](/power-platform/admin/capacity-add-on).

Przejdź do centrum [administracyjnego platformy Power Platform,](https://admin.powerplatform.microsoft.com/resources/capacity) aby sprawdzić środki i użycie.
  
## <a name="additional-term-store-features"></a>Dodatkowe funkcje magazynu okresów
 
Subskrypcja usługi SharePoint Syntex funkcje następujących dodatkowych magazynów terminów:
 
- Importowanie zestawu okresów opartego na SKOS
- Wypychanie typów zawartości przedsiębiorstwa do witryny centrum, która również dodaje je do skojarzonych witryn i wszystkich nowo utworzonych list lub bibliotek
- Raporty magazynu okresów zapewniające szczegółowe informacje o opublikowanych zestawach okresów i ich używaniu w całej dzierżawie


## <a name="see-also"></a>Zobacz też

[Omówienie licencjonowania platformy Microsoft Power Platform](/power-platform/admin/pricing-billing-skus)

[Power Apps i Power Automate — często zadawane pytania dotyczące licencjonowania](/power-platform/admin/powerapps-flow-licensing-faq)
