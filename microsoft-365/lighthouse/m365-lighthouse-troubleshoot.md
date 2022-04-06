---
title: Rozwiązywanie problemów i komunikatów o błędach w programie Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: W przypadku dostawców usług zarządzanych (MSP) używających Microsoft 365 Lighthouse uzyskaj pomoc w rozwiązywaniu problemów i komunikatach o błędach.
ms.openlocfilehash: 24f282420bb69188106178cefc6fb89968f4fcf6
ms.sourcegitcommit: 2bbccbcffce3ea6d10ea6d307349874eafb21339
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2022
ms.locfileid: "64645039"
---
# <a name="troubleshoot-and-resolve-problems-and-error-messages-in-microsoft-365-lighthouse"></a>Rozwiązywanie problemów i komunikatów o błędach w programie Microsoft 365 Lighthouse

W tym artykule opisano komunikaty o błędach i problemy, które mogą wystąpić podczas korzystania z programu Microsoft 365 Lighthouse, i przedstawiono kroki rozwiązywania problemów, które można wykonać w celu ich rozwiązania.

## <a name="partner-onboarding"></a>Dołączanie partnerów

### <a name="message-when-trying-to-access-lighthouse-microsoft-365-lighthouse-doesnt-support-indirect-providers-at-this-time-you-must-be-an-indirect-reseller-or-direct-bill-partner-to-use-this-service"></a>Komunikat podczas próby uzyskania dostępu do latarni morskiej: "Usługa Microsoft 365 Lighthouse nie obsługuje obecnie dostawców pośrednich, musisz być pośrednim odsprzedawcą lub bezpośrednim partnerem-dostawcą usług, aby korzystać z tej usługi".

**Przyczyna:** Próbowano uzyskać dostęp do latarni morskiej jako partner pośredni-rachunek. Obecnie latarnia Lighthouse obsługuje tylko pośrednich odsprzedawców i partnerów bezpośrednich faktur.

**Rozwiązanie:** Aby uzyskać pełną listę kwalifikacji i wymagań, zobacz [Wymagania dotyczące Microsoft 365 Lighthouse](m365-lighthouse-requirements.md). Jeśli nie jesteś pośrednim dostawcą i uważasz, że ta wiadomość została odebrana przez pomyłkę, skontaktuj się z pomocą techniczną. Aby uzyskać więcej informacji, [zobacz Uzyskiwanie pomocy technicznej dotyczącej Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

### <a name="message-when-trying-to-access-lighthouse-you-must-be-an-indirect-reseller-or-direct-bill-partner-to-use-this-service"></a>Komunikat podczas próby uzyskania dostępu do latarni morskiej: "Aby korzystać z tej usługi, musisz być pośrednim odsprzedawcą lub partnerem, który korzysta z tej usługi"

**Przyczyna:** Próbowano uzyskać dostęp do latarni morskiej i nie jesteś partnerem firmy Microsoft. Aby korzystać z oprogramowania Lighthouse, musisz zostać zarejestrowanym w programie Dostawca rozwiązań w chmurze (CSP) jako pośredni odsprzedawca lub partner bezpośredni.

**Rozwiązanie:** Aby uzyskać pełną listę kwalifikacji i wymagań, zobacz [Wymagania dotyczące Microsoft 365 Lighthouse](m365-lighthouse-requirements.md). Jeśli kwalifikujesz się do uzyskania dostępu do latarni morskiej i uważasz, że ta wiadomość została odebrana przez pomyłkę, skontaktuj się z pomocą techniczną. Aby uzyskać więcej informacji, [zobacz Uzyskiwanie pomocy technicznej dotyczącej Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

### <a name="message-when-signing-in-to-lighthouse-accept-the-partner-amendment"></a>Komunikat podczas logowania się do latarni morskiej: "Zaakceptuj poprawkę dla partnera"

**Przyczyna:** Próbowano uzyskać dostęp do latarni morskiej przed podpisaniem przez administratora globalnego w dzierżawie partnerskiej zgody partnera.

**Rozwiązanie:** Administrator globalny musi zalogować się w latarni morskiej i zaakceptować poprawkę dla partnera, aby można było uzyskać dostęp do latarni morskiej i pracować nad nim. Jeśli komunikat o błędzie będzie nadal występował po podpisaniu poprawki przez administratora globalnego, skontaktuj się z pomocą techniczną. Aby uzyskać więcej informacji, [zobacz Uzyskiwanie pomocy technicznej dotyczącej Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

## <a name="customer-tenant-onboarding"></a>Dołączanie do dzierżawy klienta  

### <a name="customer-tenants-show-a-status-other-than-active-in-the-tenant-list"></a>Na liście dzierżaw klientów jest pokazywany stan inny niż "Aktywny"  

**Przyczyna:** Dzierżawy Twoich klientów nie spełniają następujących kryteriów:

  - Aby zarządzać dzierżawą klienta, należy skonfigurować dostęp delegowany dla dostawcy usług zarządzanych*
  - Musi mieć co najmniej jedną Microsoft 365 Business Premium, Microsoft 365 E3 lub Windows 365 Business licencji
  - Nie może mieć więcej niż 1000 licencjonowanych użytkowników 

**Rozwiązanie:** W poniższej tabeli opisano różne stany dzierżawy wymagające działania i wyjaśniono, jak je rozwiązać.

*Delegowane uprawnienia administratora (DAP) są wymagane, aby można było dołączać klientów do usługi Lighthouse. W celu zapewnienia bardziej bezpiecznego dostępu delegowanego zalecamy także nawiązanie z klientami szczegółowych, delegowanych uprawnień administratora (GDAP, Granular Delegated Admin Privileges). Podczas gdy usługi DAP i GDAP są współistniene, GDAP będą miały pierwszeństwo dla klientów, dla których są dostępne oba modele. Wkrótce klienci, którzy mają tylko GDAP (bez protokołu DAP), będą mogli wdrapać się do latarni morskiej.


| Stan | Opis | Rozwiązanie |
|--|--|--|
| Nieaktywny | Dzierżawa została wyłączona na żądanie usługi MSP i nie jest już zarządzana w latarni morskiej. | Należy ponownie aktywować dzierżawę. Na stronie **Dzierżawy** wybierz trzy kropki (więcej akcji) obok dzierżawy, którą chcesz aktywować ponownie, a następnie wybierz pozycję **Aktywuj dzierżawę**. Może mi potrwać 24–48 godzin, aby początkowe dane klienta pojawią się w Latarnia morska. |
| Nieuczciwą — nie ustawiono protokołu DAP lub GDAP | Nie masz uprawnień administratora dap lub GDAP sfinanych z dzierżawą, co jest wymagane przez usługę Lighthouse. | Konfigurowanie uprawnień administratora dap lub GDAP w Centrum partnerskim firmy Microsoft. |
| Nieukwalifikowana — brakuje wymaganej licencji | W dzierżawie brakuje wymaganej licencji. Potrzebuje co najmniej jednej licencji Microsoft 365 Business Premium, Microsoft 365 E3 lub Windows 365 Business licencji. | Upewnij się, że dzierżawa ma przypisaną co najmniej Microsoft 365 Business Premium, Microsoft 365 E3 lub Windows 365 Business dzierżawy. |
| Bez uprawnienia — przekroczono liczbę użytkowników | Dzierżawa ma więcej niż 1000 licencjonowanych użytkowników dozwolonych przez lighthouse. | Sprawdź, czy dzierżawa nie ma więcej niż 1000 licencjonowanych użytkowników. |
| Nieukwalifikowane — sprawdzenie geolokalizacji nie powiodło się | Ty i Twój klient nie mieszkacie w tym samym regionie geograficznym, co jest wymagane przez usługę Lighthouse. | Sprawdź, czy klient znajduje się w Twoim regionie geograficznym. Jeśli nie, nie możesz zarządzać dzierżawą w latarni morskiej. |
| W trakcie procesu | Latarnia morska wykryła dzierżawę, ale nadal jest w trakcie procesu ich wyniania. | Zezwalaj na dołączanie dzierżawy do usługi Lighthouse przez 48 godzin. |

Jeśli potwierdzono, że dzierżawa Twojego klienta spełnia kryteria dołączania, i nadal nie jest ona pokazywana  jako aktywna w latarni morskiej, skontaktuj się z pomocą techniczną. Aby uzyskać więcej informacji, [zobacz Uzyskiwanie pomocy technicznej dotyczącej Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

## <a name="access-and-permissions"></a>Dostęp i uprawnienia

### <a name="message-when-trying-to-access-lighthouse-not-authorized-or-insufficient-privileges-or-access-restriction-insufficient-or-lack-of-permissions-is-causing-access-restriction"></a>Komunikat podczas próby uzyskania dostępu do latarni morskiej: "Nieu autoryzowane" lub "Niewystarczające uprawnienia" lub "Ograniczenie dostępu: Niewystarczające lub brak uprawnień powoduje ograniczenie dostępu" 

**Przyczyna:** Nie należysz do odpowiedniej grupy zabezpieczeń w usłudze Azure AD lub nie przypisano Ci odpowiedniej roli w Centrum partnerskim, aby móc uzyskać dostęp do usługi Lighthouse.

**Rozwiązanie:** Upewnij się, że administrator z Dzierżawy partnera z odpowiednimi uprawnieniami przypisał Cię do odpowiedniej grupy zabezpieczeń GDAP w usłudze Azure AD i przypisał Ci poprawną rolę w Centrum partnerskim. Pamiętaj też, że niektóre akcje w latarni morskiej wymagają, aby być administratorem globalnym. Aby dowiedzieć się więcej o rolach protokołu GDAP i poszczególnych rolach, zobacz Omówienie uprawnień w [programie Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md). Aby uzyskać szczegółowy opis wszystkich wbudowanych ról i uprawnień usługi Azure AD dla protokołu GDAP, zobacz Wbudowane role usługi [Azure AD](/azure/active-directory/roles/permissions-reference).

W przypadku klientów z relacjami daP administrator partnerów musi przypisać Ci rolę agenta administracyjnego lub agenta pomocy technicznej w Centrum partnerskim. Aby uzyskać szczegółowy opis wszystkich ról i uprawnień w Centrum partnerskim, zobacz [Przypisywanie ról i uprawnień użytkownikom](/partner-center/permissions-overview).

### <a name="i-dont-see-complete-data-in-certain-areas-of-lighthouse-or-i-cant-perform-certain-tasks-or-i-cant-access-certain-tenants"></a>Nie widzę pełnych danych w niektórych obszarach latarni morskiej lub nie mogę wykonać niektórych zadań albo nie mogę uzyskać dostępu do niektórych dzierżaw

**Przyczyna:** Dostęp do usługi GDAP jest ograniczony w zależności od ról przypisanych do grupy zabezpieczeń usługi Azure AD, w których się jesteś.

**Rozwiązanie:** Upewnij się, że administrator z dzierżawy partnera z odpowiednimi uprawnieniami przypisał Cię do odpowiedniej grupy zabezpieczeń GDAP w usłudze Azure AD. Pamiętaj też, że niektóre akcje w latarni morskiej wymagają, aby być administratorem globalnym. Aby dowiedzieć się więcej o rolach protokołu GDAP i poszczególnych rolach, zobacz Omówienie uprawnień w [programie Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md). Aby uzyskać szczegółowy opis wszystkich wbudowanych ról i uprawnień usługi Azure AD dla protokołu GDAP, zobacz Wbudowane role usługi [Azure AD](/azure/active-directory/roles/permissions-reference).

## <a name="customer-tenant-management"></a>Zarządzanie dzierżawą klientów  

### <a name="customer-tenant-has-no-data-showing-in-lighthouse"></a>Dzierżawa klienta nie ma żadnych danych pokazywanych w Latarnia morska

**Przyczyna:** Próbujesz wyświetlić dane w układzie Lighthouse przed zakończeniem dołączania dzierżawy.

**Rozwiązanie:** Może mi potrwać 24–48 godzin, aby początkowe dane klienta pojawią się w Latarnia morska. Jeśli od momentu dojechywania dzierżawy do dzierżawy mi zostało więcej niż 48 godzin i nadal nie możesz wyświetlić ani załadować danych dzierżawy albo nie możesz wyświetlić lub załadować danych, które wcześniej były możliwe, skontaktuj się z pomocą techniczną. Aby uzyskać więcej informacji, [zobacz Uzyskiwanie pomocy technicznej dotyczącej Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md). Przygotuj się do przygotowania odpowiednich dzienników sieci oraz listy wszystkich opcji, które mogą zostać zmodyfikowane.

### <a name="customer-tenant-data-isnt-updating-after-making-changes-in-the-customer-tenant"></a>Dane dzierżawy klienta nie są aktualizowane po w wprowadzenie zmian w dzierżawie klienta

**Przyczyna:** Synchronizacja zmian wprowadzonych w dzierżawie klienta może potrwać do 4 godzin na synchronizację z danymi dzierżawy klienta w latarni morskiej.

**Rozwiązanie:** Jeśli miły ponad 4 godziny, a dane dzierżawy klientów nadal nie są aktualizowane w latarni morskiej, skontaktuj się z pomocą techniczną. Aby uzyskać więcej informacji, [zobacz Uzyskiwanie pomocy technicznej dotyczącej Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md). Przygotuj się do podania informacji o dzierżawie klienta.

### <a name="message-when-applying-a-baseline-to-a-customer-tenant-process-error-occurred"></a>Komunikat podczas stosowania planu bazowego do dzierżawy klienta: "Wystąpił błąd procesu"  

**Przyczyna:** Nie ukończono pomyślnie konfiguracji programu Microsoft Intune w dzierżawie klienta.

**Rozwiązanie:** Upewnij się, że zostały wykonane podstawowe kroki konfiguracji Intune w dzierżawie klienta. Jeśli problem będzie nadal występował po sprawdzeniu, Intune że konfiguracja dzierżawy klienta jest ukończona, skontaktuj się z pomocą techniczną. Aby uzyskać więcej informacji, [zobacz Uzyskiwanie pomocy technicznej dotyczącej Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

### <a name="cant-access-partner-tenant-data-in-lighthouse"></a>Nie można uzyskać dostępu do danych dzierżawy partnera w latarni morskiej

**Przyczyna**: Latarnia morska obsługuje *tylko wyświetlanie dzierżaw* klientów i zarządzanie nimi. Obecnie nie obsługuje ona wyświetlania dzierżaw *partnerów i zarządzania* nimi.

**Rozwiązanie:** Kontynuuj korzystanie z dowolnej metody wyświetlania dzierżawy partnerskiej i zarządzania nimi.

## <a name="device-and-threat-management"></a>Zarządzanie urządzeniami i zagrożeniami 

### <a name="i-dont-see-any-customer-tenant-data-on-the-device-compliance-and-threat-management-pages-of-lighthouse"></a>Nie widzę żadnych danych dzierżawy klienta na stronach zarządzania zagrożeniami i zgodnością urządzeń w aplikacji Lighthouse

**Przyczyna 1:** Dzierżawa klienta nie ukończyła procesu dołączania do usługi Intune. Dane dzierżawy klienta nie będą dostępne na stronach zgodności urządzeń i zarządzania zagrożeniami w układzie Lighthouse, dopóki dzierżawa klienta nie ukończy do Intune.

**Rozwiązanie:** Upewnij się, że dzierżawa klienta, dla których próbujesz wyświetlić dane, zakończyła dołączanie do usługi Intune. Po zakończeniu dołączania w Intune, zezwalaj na dane urządzenia w latarni morskiej po 4 godzinach.

**Przyczyna 2:** Dzierżawa klienta została ostatnio wniesona do latarni morskiej Lighthouse i dane nadal są ładowane w latarni morskiej.

**Rozwiązanie:** Po dojściu dzierżawcy klienta do latarni morskiej zezwalaj na pierwsze dane klienta od 24 do 48 godzin.

**Przyczyna 3:** Urządzenie dzierżawy klienta jest nowe, a dane urządzeń są nadal ładowane w Latarnia morska.

**Rozwiązanie:** Po dodaniu urządzenia dzierżawcy możesz zezwolić na to, aby dane urządzenia pojawiały się w Latarnia morska po 4 godzinach.

Jeśli po zakończeniu rozwiązywania problemów dane nadal nie są wyświetlane na stronach Zgodność urządzenia i Zarządzanie zagrożeniami, skontaktuj się z pomocą techniczną. Aby uzyskać więcej informacji, [zobacz Uzyskiwanie pomocy technicznej dotyczącej Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

## <a name="related-content"></a>Zawartość pokrewna

[Znane problemy dotyczące Microsoft 365 Lighthouse](m365-lighthouse-known-issues.md) (artykuł)\
[Microsoft 365 Lighthouse faq](m365-lighthouse-faq.yml) (artykuł)\
[Uzyskiwanie pomocy technicznej dotyczącej Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md) (artykuł)