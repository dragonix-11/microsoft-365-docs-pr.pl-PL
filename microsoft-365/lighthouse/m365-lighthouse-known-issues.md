---
title: Znane problemy dotyczące Microsoft 365 Lighthouse
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
- AdminSurgePortfolib
- M365-Lighthouse
search.appverid: MET150
description: W przypadku usługi zarządzanych dostawców usług (MSP) używających Microsoft 365 Lighthouse zobacz listę znanych problemów dotyczących latarni morskiej według obszaru funkcji.
ms.openlocfilehash: 3151937d4552da09c9cfd6808db2bad8bafbbc46
ms.sourcegitcommit: 33bc25167812b31c51cf096c728e3a5854e94f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2022
ms.locfileid: "64594670"
---
# <a name="known-issues-with-microsoft-365-lighthouse"></a>Znane problemy dotyczące Microsoft 365 Lighthouse

Ten artykuł zawiera listę znanych problemów dotyczących Microsoft 365 Lighthouse według obszaru funkcji. Aby uzyskać więcej informacji o latarni morskiej, zobacz [Omówienie Microsoft 365 Lighthouse](m365-lighthouse-overview.md).

## <a name="users"></a>Użytkownicy

| Problem | Opis | Rozwiązanie |
| ---------------- | ---------------- | ---------------- |
| **Agent pomocy technicznej nie może zresetować hasła użytkownika** | Technikom zarządzanym dostawcy usług (MSP), którzy są członkami grupy Agent pomocy technicznej, nie można resetować haseł użytkowników w dzierżawach klientów. Gdy użytkownik próbuje zresetować hasło, jest wyświetlany następujący komunikat o błędzie: "Nie masz uprawnień do tego. [Dowiedz się więcej](m365-lighthouse-configure-portal-security.md)" | Aby można było pamiętać o problemie z uprawnieniami, agenci pomocy technicznej powinni resetować hasła przy użyciu Centrum administracyjne platformy Microsoft 365 lub Azure Active Directory. |

## <a name="devices"></a>Urządzenia

| Problem | Opis | Rozwiązanie |
| ---------------- | ---------------- | ---------------- |
| **Zostaną wyświetlone usunięte zasady** | Po usunięciu zasad zgodności urządzenia z Intune, będą one nadal tymczasowo widoczne w latarni morskiej. Jeśli technikom w programie MSP zostanie próba porównania zasad z usuniętymi zasadami, technikom zostanie wyświetlany następujący komunikat o błędzie: "Wystąpił problem. Odśwież stronę i spróbuj ponownie". | Aby rozwiązać ten problem, wyczyść usunięte zasady z porównania zasad i porównaj tylko istniejące zasady. |

## <a name="threat-management"></a>Zarządzanie zagrożeniami

| Problem | Opis | Rozwiązanie |
| ---------------- | ---------------- | ---------------- |
| **Brakuje nazwy zagrożenia** | Gdy technikom MSP wyświetlana jest lista zagrożeń na stronie Zarządzanie zagrożeniami, nazwa zagrożenia może nie być podnajęna przez niektóre zagrożenia. Dzieje się tak, gdy urządzenie, na którym wykryto zagrożenie, zostało ostatnio usunięte z Intune. | Ten problem zostanie rozwiązany w ciągu 48 godzin. Nie są wymagane żadne dodatkowe kroki. |

## <a name="baselines"></a>Linie bazowe

| Problem | Opis | Rozwiązanie |
| ---------------- | ---------------- | ---------------- |
| **Ustawienia powodujące konflikty podczas porównywania etapów blokowania starszego uwierzytelniania i wdrażania uwierzytelniania wieloskładnikowego** | Jeśli dzierżawa klienta wdrożyła blokowanie starszego uwierzytelniania i jeden z kroków wdrażania uwierzytelniania wieloskładnikowego, test porównania błędnie opisze te ustawienia jako powodujące konflikty. | Obejście nie jest wymagane. Ustawienia nie są w rzeczywistości powodujące konfliktu i nie ma wpływu na użytkowników w dzierżawie klienta. |

## <a name="windows-365"></a>Windows 365

| Problem | Opis | Rozwiązanie |
| ---------------- | ---------------- | ---------------- |
| **Błąd ponownego inicjowania obsługi** | Podczas próby ponownego inicjowania obsługi administracyjnej komputera w chmurze technikom jest wyświetlany komunikat o błędzie "Nie masz uprawnień do tego". | Aby around this issue, sign in to the customer tenant and then reprovision Cloud PCs from the Microsoft Endpoint Manger admin center. Aby uzyskać instrukcje, [zobacz Ponowne przewidujenie obsługi komputera w chmurze](/windows-365/enterprise/reprovision-cloud-pc). |

## <a name="audit-logs"></a>Dzienniki inspekcji


| Problem | Opis | Rozwiązanie |
|--|--|--|
| **Akcje dezaktywuj i aktywuj ponownie nie są wyświetlane w dziennikach inspekcji** | Następujące działania nie są obecnie zgłaszane na stronie Dzienniki inspekcji w latarni morskiej: <ul><li>Nazwa: akcja offboardTenant \| : dezaktywowanie klienta</li> <li>Nazwa: resetTenantOnboardingStatus \| Action: Reactive customer</li></ul> | Nie ma obejścia, ale pracujemy nad jego rozwiązaniem. Te działania będą wyświetlane w dziennikach inspekcji po wdrożeniu poprawki w usłudze. |
| **Filtr nie wyświetla wszystkich użytkowników** | Gdy technikom w programie MSP są próbowane filtrowanie przy użyciu instrukcji **Zainicjowane** przez, lista wszystkich głównych nazw użytkowników (UPN) — odpowiadających identyfikatorom poczty e-mail techników, którzy zainicjowali akcje generujące dzienniki inspekcji — nie jest w pełni wyświetlana w obszarze filtru.<br><br>Należy pamiętać, że same dzienniki inspekcji będą w pełni wyświetlane. wpływa tylko na możliwość ich filtrowania przy użyciu **zainicjowanych** przez. | Nie ma obejścia, ale pracujemy nad jego rozwiązaniem. Po wdrożeniu poprawki w usłudze filtr zostanie przywrócony do oczekiwanego zachowania — wyświetlanie pełnej listy upnów, według których mają być filtrowane. |

## <a name="delegated-admin-privilegesdap"></a>Uprawnienia administratora delegowanego (DAP)

| Problem | Opis | Rozwiązanie |
| ---------------- | ---------------- | ---------------- |
| **Opóźnienie uprawnień podczas zmieniania ról daP** | Jeśli technik MSP zostanie dodany do grupy agentów administracyjnych lub agenta pomocy technicznej lub usunięty z tej grupy, może na tym wystąpić opóźnienie w odzwierciedleniu odpowiednich uprawnień w latarni morskiej. | Ten problem zostanie rozwiązany w ciągu 30 minut. Nie są wymagane żadne dodatkowe kroki. |

## <a name="granular-delegated-admin-privilegesgdap"></a>Szczegółowe, delegowane uprawnienia administratora (GDAP)

> [!NOTE]
> GDAP jest obecnie w [wersji Technical Preview (publiczna](/partner-center/announcements/2022-february#6) wersja Zapoznawcza), aby umożliwić partnerom przypisywanie szczegółowych uprawnień przed ogólnym dostępem do usługi GDAP.

Obecnie, aby klienci korzystający z usługi Lighthouse korzystali z usługi Lighthouse, jest ona wymagana. Zalecamy również ustanowienie protokołu GDAP ze swoimi klientami, aby umożliwić bezpieczniejszy dostęp delegowany. Podczas gdy usługi DAP i GDAP są współistniene, GDAP będą miały pierwszeństwo dla klientów, dla których są dostępne oba modele. Wkrótce klienci, którzy mają tylko GDAP (bez protokołu DAP), będą mogli wdrapać się do latarni morskiej.<br><br>

| Problem | Opis | Rozwiązanie |
| ---------------- | ---------------- | ---------------- |
| **Różne problemy z uprawnieniami GDAP w latarni morskiej** | Niektóre role GDAP samodzielnie nie przyznają dostępu do danych klientów w latarni lighthouse tak samo, jak w przypadku obsługi z jedną dzierżawą. Jeśli technikom MSP przypisano dowolną z następujących ról (nie jest to w połączeniu z innymi rolami GDAP), mogą napotkać błędy, takie jak:<ul><li>Administratorzy zabezpieczeń GDAP nie mogą wyświetlać ryzykownych użytkowników, odrzucać zagrożeń ani potwierdzać naruszonych użytkowników w aplikacji Lighthouse.</li><li>Czytniki zabezpieczeń GDAP nie mogą wyświetlać ryzykownych użytkowników w latarni morskiej.</li><li>Administratorzy globalni GDAP widzą komunikat o błędzie podczas próby wyświetlenia kondycji usługi w usłudze Lighthouse.</li><li>Administratorzy globalni GDAP doświadczają problemów podczas wdrażania planu wdrożenia w latarni morskiej.</li></ul> | Aby obejść ten problem, przypisz kombinację ról GDAP technikom MSP w zależności od poziomu dostępu do potrzebnych danych klienta. Aby uzyskać listę zalecanych ról GDAP do korzystania z usługi Lighthouse, zobacz Omówienie uprawnień w [programie Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md).<br><br>W przypadku problemów, w których nawet uprawnienia administratora globalnego GDAP nie zezwalają na użycie funkcji w latarni morskiej, obejściem tego problemu jest uzyskanie dostępu do odpowiedniego centrum administracyjnego w dzierżawie klienta w celu zarządzania klientem (na przykład uzyskania dostępu do usługi Centrum administracyjne platformy Microsoft 365 z dzierżawy klienta w celu sprawdzenia kondycji usługi). Aby uzyskać instrukcje dotyczące modyfikowania relacji GDAP, zobacz Uzyskiwanie szczegółowych uprawnień administratora w celu zarządzania usługą klienta [— Centrum partnerskie.](/partner-center/gdap-obtain-admin-permissions-to-manage-customer) |

## <a name="localization"></a>Lokalizacja

| Problem | Opis | Rozwiązanie |
| ---------------- | ---------------- | ---------------- |
| **Problemy z tłumaczeniami** | Użytkownicy mogą doświadczać problemów z tłumaczeniem języków, gdy język przeglądarki lub ich wybór języka w latarnice morski jest niczym innym niż angielski. | Aby zminimalizować problemy z tłumaczeniami w latarni morskiej, upewnij się, że wybór języka przeglądarki jest taki, jak w przypadku ustawienia języka w portalu Lighthouse. Aby zmienić wybór języka w latarni morskiej, zaloguj się do lighthouse i wybierz ikonę koła zębatego u góry strony, aby otworzyć stronę ustawień portalu, wybierz pozycję Język **+ region**, a następnie wybierz odpowiednie formaty językowe i regionalne. |

## <a name="related-content"></a>Zawartość pokrewna

[Microsoft 365 Lighthouse faq](m365-lighthouse-faq.yml) (artykuł)\
[Rozwiązywanie problemów i komunikatów o błędach w programie Microsoft 365 Lighthouse](m365-lighthouse-troubleshoot.md) (artykuł)\
[Uzyskiwanie pomocy technicznej dotyczącej Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md) (artykuł)