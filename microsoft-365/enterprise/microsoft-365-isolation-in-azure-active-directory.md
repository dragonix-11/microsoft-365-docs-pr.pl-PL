---
title: izolacja Microsoft 365 i Access Control w Azure Active Directory
ms.author: robmazz
author: robmazz
manager: scotv
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
description: W tym artykule dowiesz się, jak izolacja i Access Control działają w celu odizolowania danych dla wielu dzierżaw w ramach Azure Active Directory.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 409528847d04a55926138e49128f018b349da0a3
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093882"
---
# <a name="microsoft-365-isolation-and-access-control-in-azure-active-directory"></a>izolacja Microsoft 365 i Access Control w Azure Active Directory

Azure Active Directory (Azure AD) została zaprojektowana do hostowania wielu dzierżaw w wysoce bezpieczny sposób za pośrednictwem logicznej izolacji danych. Dostęp do usługi Azure AD jest objęty warstwą autoryzacji. Usługa Azure AD izoluje klientów przy użyciu kontenerów dzierżaw jako granic zabezpieczeń w celu ochrony zawartości klienta, aby współdostępni współdostępni nie mogli uzyskać do niej dostępu ani naruszyć jej zabezpieczeń. Trzy testy są wykonywane przez warstwę autoryzacji usługi Azure AD:

- Czy podmiot zabezpieczeń jest włączony w celu uzyskania dostępu do dzierżawy usługi Azure AD?
- Czy podmiot zabezpieczeń jest włączony w celu uzyskania dostępu do danych w tej dzierżawie?
- Czy rola podmiotu zabezpieczeń w tej dzierżawie jest autoryzowana dla typu żądanego dostępu do danych?

Żadna aplikacja, użytkownik, serwer ani usługa nie mogą uzyskiwać dostępu do usługi Azure AD bez odpowiedniego uwierzytelniania, tokenu lub certyfikatu. Żądania są odrzucane, jeśli nie towarzyszą im odpowiednie poświadczenia.

W praktyce usługa Azure AD hostuje każdą dzierżawę we własnym chronionym kontenerze z zasadami i uprawnieniami do i w kontenerze należącym wyłącznie do dzierżawy i zarządzanym przez dzierżawę.
 
![Kontener platformy Azure.](../media/office-365-isolation-azure-container.png)

Koncepcja kontenerów dzierżawy jest głęboko zakorzeniona w usłudze katalogowej we wszystkich warstwach, od portali aż po magazyn trwały. Nawet jeśli wiele metadanych dzierżawy usługi Azure AD jest przechowywanych na tym samym dysku fizycznym, nie ma relacji między kontenerami innymi niż zdefiniowane przez usługę katalogową, co z kolei jest podyktowane przez administratora dzierżawy. Nie można nawiązać bezpośrednich połączeń z magazynem usługi Azure AD z dowolnej aplikacji lub usługi, bez uprzedniego przejścia przez warstwę autoryzacji.

W poniższym przykładzie zarówno firma Contoso, jak i firma Fabrikam mają oddzielne, dedykowane kontenery i mimo że te kontenery mogą współużytkować niektóre z tych samych podstawowych infrastruktur, takich jak serwery i magazyny, pozostają oddzielone i odizolowane od siebie i otoczone warstwami autoryzacji i kontroli dostępu.
 
![Dedykowane kontenery platformy Azure.](../media/office-365-isolation-azure-dedicated-containers.png)

Ponadto nie ma żadnych składników aplikacji, które mogą być wykonywane z poziomu usługi Azure AD i nie jest możliwe, aby jedna dzierżawa wymusiła naruszenie integralności innej dzierżawy, dostęp do kluczy szyfrowania innej dzierżawy lub odczytanie nieprzetworzonych danych z serwera.

Domyślnie usługa Azure AD nie zezwala na wszystkie operacje wystawiane przez tożsamości w innych dzierżawach. Każda dzierżawa jest logicznie izolowana w usłudze Azure AD za pośrednictwem kontroli dostępu opartej na oświadczeniach. Odczyty i zapisy danych katalogów są ograniczone do kontenerów dzierżawy i objęte wewnętrzną warstwą abstrakcji oraz warstwą kontroli dostępu opartą na rolach (RBAC), które razem wymuszają dzierżawę jako granicę zabezpieczeń. Każde żądanie dostępu do danych katalogu jest przetwarzane przez te warstwy, a każde żądanie dostępu w Microsoft 365 jest obsługiwane przez powyższą logikę.

Usługa Azure AD ma partycje Ameryka Północna, Us Government, European Union, Germany i World Wide. Dzierżawa istnieje w jednej partycji, a partycje mogą zawierać wiele dzierżaw. Informacje o partycjach są abstrakcyjne dla użytkowników. Dana partycja (w tym wszystkie dzierżawy w niej) jest replikowana do wielu centrów danych. Partycja dla dzierżawy jest wybierana na podstawie właściwości dzierżawy (np. kodu kraju). Wpisy tajne i inne informacje poufne w każdej partycji są szyfrowane za pomocą dedykowanego klucza. Klucze są generowane automatycznie po utworzeniu nowej partycji.

Funkcje systemu usługi Azure AD są unikatowym wystąpieniem dla każdej sesji użytkownika. Ponadto usługa Azure AD używa technologii szyfrowania w celu zapewnienia izolacji udostępnionych zasobów systemowych na poziomie sieci, aby zapobiec nieautoryzowanemu i niezamierzonemu transferowi informacji.
