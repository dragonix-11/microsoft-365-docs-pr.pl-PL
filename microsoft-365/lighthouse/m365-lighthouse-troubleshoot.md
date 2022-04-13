---
title: Rozwiązywanie problemów i komunikatów o błędach w Microsoft 365 Lighthouse
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
description: W przypadku dostawców usług zarządzanych korzystających z Microsoft 365 Lighthouse uzyskaj pomoc dotyczącą rozwiązywania problemów i komunikatów o błędach.
ms.openlocfilehash: 1126db76129a0f3cf6b65921a6e731f02d7311d3
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824075"
---
# <a name="troubleshoot-and-resolve-problems-and-error-messages-in-microsoft-365-lighthouse"></a>Rozwiązywanie problemów i komunikatów o błędach w Microsoft 365 Lighthouse

W tym artykule opisano komunikaty o błędach i problemy, które mogą wystąpić podczas korzystania z Microsoft 365 Lighthouse, oraz przedstawiono kroki rozwiązywania problemów, które można podjąć w celu ich rozwiązania.

## <a name="partner-onboarding"></a>Dołączanie partnerów

### <a name="message-when-trying-to-access-lighthouse-microsoft-365-lighthouse-doesnt-support-indirect-providers-at-this-time-you-must-be-an-indirect-reseller-or-direct-bill-partner-to-use-this-service"></a>Komunikat podczas próby uzyskania dostępu do usługi Lighthouse: "Microsoft 365 Lighthouse obecnie nie obsługuje dostawców pośrednich, musisz być odsprzedawcą pośrednim lub partnerem rozliczeń bezpośrednich, aby korzystać z tej usługi"

**Spowodować:** Próbowano uzyskać dostęp do usługi Lighthouse jako partner rozliczeń pośrednich. Obecnie usługa Lighthouse obsługuje tylko odsprzedawców pośrednich i partnerów rozliczających się bezpośrednio.

**Rozdzielczość:** Aby uzyskać pełną listę kwalifikacji i wymagań, zobacz [Wymagania dotyczące Microsoft 365 Lighthouse](m365-lighthouse-requirements.md). Jeśli nie jesteś dostawcą pośrednim i uważasz, że ten komunikat został wyświetlony o błędzie, skontaktuj się z pomocą techniczną. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie pomocy i obsługi technicznej dotyczącej Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

### <a name="message-when-trying-to-access-lighthouse-you-must-be-an-indirect-reseller-or-direct-bill-partner-to-use-this-service"></a>Komunikat podczas próby uzyskania dostępu do usługi Lighthouse: "Aby móc korzystać z tej usługi, musisz być odsprzedawcą pośrednim lub partnerem rozliczającym się bezpośrednio"

**Spowodować:** Podjęto próbę uzyskania dostępu do usługi Lighthouse i nie jesteś partnerem firmy Microsoft. Aby korzystać z usługi Lighthouse, musisz być zarejestrowany w programie Dostawca rozwiązań w chmurze (CSP) jako odsprzedawca pośredni lub partner rozliczeń bezpośrednich.

**Rozdzielczość:** Aby uzyskać pełną listę kwalifikacji i wymagań, zobacz [Wymagania dotyczące Microsoft 365 Lighthouse](m365-lighthouse-requirements.md). Jeśli kwalifikujesz się do uzyskania dostępu do usługi Lighthouse i uważasz, że ten komunikat został wyświetlony o błędzie, skontaktuj się z pomocą techniczną. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie pomocy i obsługi technicznej dotyczącej Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

### <a name="message-when-signing-in-to-lighthouse-accept-the-partner-amendment"></a>Komunikat podczas logowania się do lighthouse: "Zaakceptuj poprawkę partnera"

**Spowodować:** Próbowano uzyskać dostęp do usługi Lighthouse, zanim administrator globalny w dzierżawie partnera podpisał poprawkę partnera.

**Rozdzielczość:** Administrator globalny musi zalogować się do aplikacji Lighthouse i zaakceptować poprawkę partnera, zanim będzie można uzyskać dostęp do aplikacji Lighthouse i pracować w niej. Jeśli błąd będzie się powtarzać po podpisaniu poprawki przez administratora globalnego, skontaktuj się z pomocą techniczną. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie pomocy i obsługi technicznej dotyczącej Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

## <a name="customer-tenant-onboarding"></a>Dołączanie dzierżawy klienta  

### <a name="customer-tenants-show-a-status-other-than-active-in-the-tenant-list"></a>Dzierżawy klientów pokazują stan inny niż "Aktywny" na liście dzierżaw  

**Spowodować:** Dzierżawy klientów nie spełniają następujących kryteriów:

- Aby można było zarządzać dzierżawą klienta, musi mieć skonfigurowany dostęp delegowany dla dostawcy usług zarządzanych (MSP).
- Musi mieć co najmniej jedną licencję Microsoft 365 Business Premium, Microsoft 365 E3 lub Windows 365 Business
- Nie może mieć więcej niż 1000 licencjonowanych użytkowników 

**Rozdzielczość:** W poniższej tabeli opisano różne stany dzierżawy, które wymagają akcji, i wyjaśniono, jak je rozwiązać.

*Uprawnienia administratora delegowanego (DAP) są wymagane do dołączenia klientów do usługi Lighthouse. Zalecamy również ustanowienie szczegółowych uprawnień administratora delegowanego (GDAP) z klientami, aby umożliwić bezpieczniejszy dostęp delegowany. Chociaż dap i GDAP współistnieją, GDAP będzie mieć pierwszeństwo dla klientów, gdzie oba modele są w miejscu. Wkrótce klienci z zaledwie GDAP (i bez dap) będą mogli dołączyć do lighthouse.

| Stan | Opis | Rozwiązanie |
|--|--|--|
| Nieaktywne | Dzierżawa została odłączona na żądanie MSP i nie jest już zarządzana w lighthouse. | Musisz ponownie uaktywnić dzierżawę. Na stronie **Dzierżawy wybierz trzy kropki** (więcej akcji) obok dzierżawy, którą chcesz ponownie uaktywnić, a następnie wybierz pozycję **Aktywuj dzierżawę**. Może upłynąć 24–48 godzin, aż początkowe dane klientów pojawią się w aplikacji Lighthouse. |
| Niekwalifikowalne — nie skonfigurowano protokołu DAP lub GDAP | Nie masz uprawnień administratora protokołu DAP ani GDAP skonfigurowanych w dzierżawie, co jest wymagane przez usługę Lighthouse. | Skonfiguruj uprawnienia administratora protokołu DAP lub GDAP w Centrum partnerskim firmy Microsoft. |
| Niekwalifikowalne — brak wymaganej licencji | W dzierżawie brakuje wymaganej licencji. Potrzebują co najmniej jednej licencji Microsoft 365 Business Premium, Microsoft 365 E3 lub Windows 365 Business. | Upewnij się, że dzierżawa ma przypisaną co najmniej jedną licencję Microsoft 365 Business Premium, Microsoft 365 E3 lub Windows 365 Business. |
| Niekwalifikowalne — przekroczono liczbę użytkowników | Dzierżawa ma więcej niż maksymalnie 1000 licencjonowanych użytkowników dozwolonych przez usługę Lighthouse. | Sprawdź, czy dzierżawa nie ma więcej niż 1000 licencjonowanych użytkowników. |
| Niekwalifikowalne — sprawdzanie geograficzne nie powiodło się | Ty i Twój klient nie mieszkacie w tym samym regionie geograficznym, który jest wymagany przez usługę Lighthouse. | Sprawdź, czy klient znajduje się w twoim regionie geograficznym. Jeśli nie, nie możesz zarządzać dzierżawą w aplikacji Lighthouse. |
| W toku | Lighthouse odkrył dzierżawę, ale nadal jest w trakcie ich dołączania. | Zezwalaj aplikacji Lighthouse na 48 godzin na ukończenie dołączania dzierżawy. |

Jeśli potwierdzisz, że dzierżawa klienta spełnia kryteria dołączania i nadal nie jest wyświetlana jako **Aktywna** w aplikacji Lighthouse, skontaktuj się z pomocą techniczną. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie pomocy i obsługi technicznej dotyczącej Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

## <a name="access-and-permissions"></a>Dostęp i uprawnienia

### <a name="message-when-trying-to-access-lighthouse-not-authorized-or-insufficient-privileges-or-access-restriction-insufficient-or-lack-of-permissions-is-causing-access-restriction"></a>Komunikat podczas próby uzyskania dostępu do usługi Lighthouse: "Nie autoryzowane" lub "Niewystarczające uprawnienia" lub "Ograniczenie dostępu: Niewystarczające lub brak uprawnień powoduje ograniczenie dostępu" 

**Spowodować:** Nie należysz do odpowiedniej grupy zabezpieczeń w usłudze Azure AD lub nie masz przypisanej prawidłowej roli w Centrum partnerskim, aby móc uzyskać dostęp do usługi Lighthouse.

**Rozdzielczość:** Upewnij się, że administrator z dzierżawy partnera z odpowiednimi uprawnieniami przydzielił Cię do odpowiedniej grupy zabezpieczeń GDAP w usłudze Azure AD i przypisze Ci poprawną rolę w Centrum partnerskim. Należy również pamiętać, że niektóre akcje w aplikacji Lighthouse wymagają uprawnień administratora globalnego. Aby dowiedzieć się więcej na temat ról GDAP i możliwości poszczególnych ról, zobacz [Omówienie uprawnień w Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md). Aby uzyskać szczegółowy opis wszystkich wbudowanych ról i uprawnień usługi Azure AD dla protokołu GDAP, zobacz [Role wbudowane usługi Azure AD](/azure/active-directory/roles/permissions-reference).

W przypadku klientów z relacjami dap administrator partnera będzie musiał przypisać Cię do roli agenta administratora lub agenta pomocy technicznej w Centrum partnerskim. Aby uzyskać szczegółowy opis wszystkich ról i uprawnień Centrum partnerskiego, zobacz [Przypisywanie ról i uprawnień użytkownikom](/partner-center/permissions-overview).

### <a name="i-dont-see-complete-data-in-certain-areas-of-lighthouse-or-i-cant-perform-certain-tasks-or-i-cant-access-certain-tenants"></a>Nie widzę pełnych danych w niektórych obszarach usługi Lighthouse, nie mogę wykonywać pewnych zadań lub nie mogę uzyskać dostępu do niektórych dzierżaw

**Spowodować:** Masz ograniczony dostęp GDAP na podstawie ról przypisanych do grupy zabezpieczeń usługi Azure AD, w której się znajdujesz.

**Rozdzielczość:** Upewnij się, że administrator z dzierżawy partnera z odpowiednimi uprawnieniami przypisył Cię do odpowiedniej grupy zabezpieczeń GDAP w usłudze Azure AD. Należy również pamiętać, że niektóre akcje w aplikacji Lighthouse wymagają uprawnień administratora globalnego. Aby dowiedzieć się więcej na temat ról GDAP i możliwości poszczególnych ról, zobacz [Omówienie uprawnień w Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md). Aby uzyskać szczegółowy opis wszystkich wbudowanych ról i uprawnień usługi Azure AD dla protokołu GDAP, zobacz [Role wbudowane usługi Azure AD](/azure/active-directory/roles/permissions-reference).

## <a name="customer-tenant-management"></a>Zarządzanie dzierżawą klienta  

### <a name="customer-tenant-has-no-data-showing-in-lighthouse"></a>Dzierżawa klienta nie ma żadnych danych wyświetlanych w usłudze Lighthouse

**Spowodować:** Próbujesz wyświetlić dane w usłudze Lighthouse przed zakończeniem dołączania dzierżawy.

**Rozdzielczość:** Może upłynąć 24–48 godzin, aż początkowe dane klientów pojawią się w aplikacji Lighthouse. Jeśli od momentu dołączenia dzierżawy do dzierżawy minęło ponad 48 godzin i nadal nie możesz wyświetlać ani ładować danych dzierżawy albo nie możesz wyświetlić ani załadować danych, które były wcześniej możliwe, skontaktuj się z pomocą techniczną. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie pomocy i obsługi technicznej dotyczącej Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md). Przygotuj się do udostępnienia odpowiednich dzienników sieciowych i listy wszystkich opcji, które mogły zostać zmodyfikowane.

### <a name="customer-tenant-data-isnt-updating-after-making-changes-in-the-customer-tenant"></a>Dane dzierżawy klienta nie są aktualizowane po wprowadzeniu zmian w dzierżawie klienta

**Spowodować:** Synchronizacja zmian wprowadzonych wewnątrz dzierżawy klienta może potrwać do 4 godzin z danymi dzierżawy klienta w aplikacji Lighthouse.

**Rozdzielczość:** Jeśli minęło więcej niż 4 godziny, a dane dzierżawy klienta nadal nie są aktualizowane w aplikacji Lighthouse, skontaktuj się z pomocą techniczną. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie pomocy i obsługi technicznej dotyczącej Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md). Przygotuj się na podanie informacji o dzierżawie klienta.

### <a name="message-when-applying-a-baseline-to-a-customer-tenant-process-error-occurred"></a>Komunikat podczas stosowania punktu odniesienia do dzierżawy klienta: "Wystąpił błąd procesu"  

**Spowodować:** Konfiguracja Microsoft Intune w dzierżawie klienta nie została pomyślnie ukończona.

**Rozdzielczość:** Sprawdź, czy wykonano podstawowe kroki konfiguracji dla Intune w dzierżawie klienta. Jeśli problem będzie się powtarzać po sprawdzeniu, czy konfiguracja Intune została ukończona dla dzierżawy klienta, skontaktuj się z pomocą techniczną. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie pomocy i obsługi technicznej dotyczącej Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

### <a name="cant-access-partner-tenant-data-in-lighthouse"></a>Nie można uzyskać dostępu do danych dzierżawy partnera w aplikacji Lighthouse

**Przyczyna**: Usługa Lighthouse obsługuje tylko wyświetlanie dzierżaw *klientów* i zarządzanie nimi. Obecnie nie obsługuje wyświetlania dzierżaw *partnerów* ani zarządzania nimi.

**Rozdzielczość:** Kontynuuj korzystanie z dowolnej metody używanej do wyświetlania dzierżawy partnera i zarządzania nią.

## <a name="device-and-threat-management"></a>Zarządzanie urządzeniami i zagrożeniami 

### <a name="i-dont-see-any-customer-tenant-data-on-the-device-compliance-and-threat-management-pages-of-lighthouse"></a>Nie widzę żadnych danych dzierżawy klienta na stronach Zgodność urządzenia i Zarządzanie zagrożeniami w aplikacji Lighthouse

**Przyczyna 1:** Dzierżawa klienta nie zakończyła dołączania do Intune. Dane dzierżawy klienta nie będą dostępne na stronach Zgodność urządzenia lub Zarządzanie zagrożeniami w aplikacji Lighthouse, dopóki dzierżawa klienta nie zakończy dołączania do Intune.

**Rozdzielczość:** Sprawdź, czy dzierżawa klienta, dla której próbujesz wyświetlić dane, zakończyła dołączanie do Intune. Po zakończeniu dołączania w Intune poczekaj 4 godziny na wyświetlenie danych urządzenia w usłudze Lighthouse.

**Przyczyna 2:** Dzierżawa klienta została niedawno dołączona do usługi Lighthouse, a dane są nadal ładowane w lighthouse.

**Rozdzielczość:** Po dołączeniu dzierżawy klienta do usługi Lighthouse poczekaj od 24 do 48 godzin na wyświetlenie początkowych danych klienta.

**Przyczyna 3:** Urządzenie dzierżawy klienta jest nowe, a dane urządzenia są nadal ładowane w usłudze Lighthouse.

**Rozdzielczość:** Po dodaniu urządzenia dzierżawy zaczekaj 4 godziny na wyświetlenie danych urządzenia w usłudze Lighthouse.

Jeśli dane nadal nie są wyświetlane na stronach Zgodność urządzenia i Zarządzanie zagrożeniami po wykonaniu instrukcji rozwiązywania problemów, skontaktuj się z pomocą techniczną. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie pomocy i obsługi technicznej dotyczącej Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

## <a name="related-content"></a>Zawartość pokrewna

[Znane problemy z Microsoft 365 Lighthouse](m365-lighthouse-known-issues.md) (artykuł)\
[Microsoft 365 Lighthouse często zadawane pytania](m365-lighthouse-faq.yml) (artykuł)\
[Uzyskiwanie pomocy i obsługi technicznej dla Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md) (artykuł)
