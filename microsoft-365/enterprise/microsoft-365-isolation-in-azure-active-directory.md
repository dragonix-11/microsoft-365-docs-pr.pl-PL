---
title: Microsoft 365 i kontrola dostępu w programie Azure Active Directory
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: W tym artykule dowiesz się, jak działa kontrola izolacji i dostępu w celu przechowywania danych dla wielu dzierżaw oddzielonych od siebie w Azure Active Directory.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 11c2c488f0168815a1485f5833c5520259db0fa5
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984450"
---
# <a name="microsoft-365-isolation-and-access-control-in-azure-active-directory"></a>Microsoft 365 i kontrola dostępu w programie Azure Active Directory

Azure Active Directory (Azure AD) zaprojektowano, aby hostować wiele dzierżaw w wysoce bezpieczny sposób dzięki izolacji danych logicznych. Dostęp do usługi Azure AD jest bramowany przez warstwę autoryzacji. Usługa Azure AD odizoluje klientów, używając kontenerów dzierżawy jako granic zabezpieczeń w celu zabezpieczenia zawartości klienta, aby współdostępniacy nie uzyskiwali dostępu do zawartości ani jej nie mogą być naruszone. Warstwa autoryzacji usługi Azure AD wykonuje trzy testy:

- Czy dla podmiotu głównego włączono dostęp do dzierżawy usługi Azure AD?
- Czy dla podmiotu głównego włączono dostęp do danych w tej dzierżawie?
- Czy rola dyrektora w tej dzierżawie jest autoryzowana dla typu żądanego dostępu do danych?

Żadna aplikacja, użytkownik, serwer ani usługa nie mogą uzyskać dostępu do usługi Azure AD bez odpowiedniego uwierzytelniania i tokenu lub certyfikatu. Żądania są odrzucane, jeśli nie towarzyszy im poświadczeń odpowiednich.

W praktyce usługa Azure AD hostuje każdą dzierżawę w własnym chronionym kontenerze, z zasadami i uprawnieniami do kontenera wyłącznie będącego własnością dzierżawy i zarządzanego przez nie.
 
![Kontener platformy Azure.](../media/office-365-isolation-azure-container.png)

Pojęcie kontenerów dzierżawy jest mocno składowane w usłudze katalogowej na wszystkich warstwach, od portali po magazyn trwały. Nawet jeśli na tym samym dysku fizycznym jest przechowywanych wiele metadanych dzierżawy usługi Azure AD, nie ma żadnej relacji między kontenerami innymi niż te zdefiniowane przez usługę katalogową, która z kolei jest dyktowana przez administratora dzierżawy. Nie może być żadnych bezpośrednich połączeń z magazynem usługi Azure AD z dowolnej żądanej aplikacji lub usługi bez uprzedniego przejść przez warstwę autoryzacji.

W poniższym przykładzie firmy Contoso i Fabrikam mają osobne dedykowane kontenery i mimo że te kontenery mogą współużytkować część tej samej infrastruktury źródłowej, na przykład serwery i magazyn, pozostają one oddzielone i odizolowane od siebie, a ponadto są przechowane przez warstwy autoryzacji i kontroli dostępu.
 
![Kontenery dedykowane platformy Azure.](../media/office-365-isolation-azure-dedicated-containers.png)

Ponadto nie ma składników aplikacji, które mogą być wykonywane z poziomu usługi Azure AD, i nie jest możliwe, aby jedna dzierżawa w sposób natłęczyła integralność innej dzierżawy, uzyskać dostęp do kluczy szyfrowania innej dzierżawy ani odczytać nieprzetworzonych danych z serwera.

Domyślnie usługa Azure AD nie zezwala na wszystkie operacje wykonywane przez tożsamości w innych dzierżawach. Każda dzierżawa jest logicznie odizolowana w usłudze Azure AD za pomocą formantów dostępu opartych na oświadczeniach. Odczyt i zapis danych katalogu jest ograniczony do kontenerów dzierżawy i jest przechowany przez wewnętrzną warstwę abstrakcyjną oraz warstwę kontroli dostępu opartej na rolach (RBAC, role based access control), która razem wymusza dzierżawę jako granicę zabezpieczeń. Każde żądanie dostępu do danych katalogu jest przetwarzane przez te warstwy, a każde żądanie dostępu w programie Microsoft 365 jest przesądowane przez logikę podaną powyżej.

Usługa Azure AD ma partycje Ameryki Północnej, Rząd Stanów Zjednoczonych, Unii Europejskiej, Niemiec i Świata. Dzierżawa istnieje na jednej partycji, a partycje mogą zawierać wiele dzierżaw. Informacje o partycji są wyimowane z dala od użytkowników. Partycja (łącznie ze wszystkimi dzierżawami na tej partycji) jest replikowana do wielu centrów danych. Partycja dzierżawy jest wybierana na podstawie właściwości dzierżawy (np. kodu kraju). Tajemnice i inne poufne informacje na poszczególnych partycjach są szyfrowane przy użyciu klucza dedykowanego. Klucze są generowane automatycznie podczas tworzenia nowej partycji.

Funkcje systemu usługi Azure AD są unikatowym wystąpieniem dla każdej sesji użytkownika. Ponadto usługa Azure AD używa technologii szyfrowania w celu zapewnienia izolacji udostępnionych zasobów systemowych na poziomie sieci, aby zapobiec nieautoryzowanemu i niezamierzonemu przesyłaniu informacji.
