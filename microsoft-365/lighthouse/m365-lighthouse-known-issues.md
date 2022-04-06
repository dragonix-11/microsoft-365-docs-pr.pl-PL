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
ms.openlocfilehash: 4d19051de1b4466dabc535446182c7f630ee948b
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2022
ms.locfileid: "63705400"
---
# <a name="known-issues-with-microsoft-365-lighthouse"></a>Znane problemy dotyczące Microsoft 365 Lighthouse

Ten artykuł zawiera listę znanych problemów dotyczących Microsoft 365 Lighthouse według obszaru funkcji. Aby uzyskać więcej informacji o latarni morskiej, zobacz [Omówienie Microsoft 365 Lighthouse](m365-lighthouse-overview.md).

## <a name="users"></a>Użytkownicy

| Problem | Opis | Rozwiązanie |
| ---------------- | ---------------- | ---------------- |
| **Agent pomocy technicznej nie może zresetować hasła użytkownika** | Technikom zarządzanym dostawcy usług (MSP), którzy są członkami grupy Agent pomocy technicznej, nie można resetować haseł użytkowników w dzierżawach klientów. Gdy użytkownik próbuje zresetować hasło, jest wyświetlany następujący komunikat o błędzie: "Nie masz uprawnień do tego. [Dowiedz się więcej](m365-lighthouse-configure-portal-security.md)" | Aby można było już pamiętać o problemie z uprawnieniami, agenci pomocy technicznej powinni resetować hasła za pomocą centrum administracyjne platformy Microsoft 365 lub Azure Active Directory. |

## <a name="devices"></a>Urządzenia

| Problem | Opis | Rozwiązanie |
| ---------------- | ---------------- | ---------------- |
| **Zostaną wyświetlone usunięte zasady** | Po usunięciu zasad zgodności urządzenia z usługi Intune, będą one tymczasowo nadal widoczne w usłudze Lighthouse. Jeśli technikom w programie MSP zostanie próba porównania zasad z usuniętymi zasadami, technikom zostanie wyświetlany następujący komunikat o błędzie: "Wystąpił problem. Odśwież stronę i spróbuj ponownie". | Aby rozwiązać ten problem, wyczyść usunięte zasady z porównania zasad i porównaj tylko istniejące zasady. |

## <a name="threat-management"></a>Zarządzanie zagrożeniami

| Problem | Opis | Rozwiązanie |
| ---------------- | ---------------- | ---------------- |
| **Brakuje nazwy zagrożenia** | Gdy technikom MSP wyświetlana jest lista zagrożeń na stronie Zarządzanie zagrożeniami, nazwa zagrożenia może nie być podnajęna przez niektóre zagrożenia. Dzieje się tak, gdy urządzenie, na którym wykryto zagrożenie, zostało ostatnio usunięte z usługi Intune. | Ten problem zostanie rozwiązany w ciągu 48 godzin. Nie są wymagane żadne dodatkowe kroki. |

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

## <a name="delegated-admin-permissionsdap"></a>Uprawnienia administratora delegowanego (DAP)

| Problem | Opis | Rozwiązanie |
| ---------------- | ---------------- | ---------------- |
| **Opóźnienie uprawnień podczas zmieniania ról daP** | Jeśli technik MSP zostanie dodany do grupy agentów administracyjnych lub agenta pomocy technicznej lub usunięty z tej grupy, może na tym wystąpić opóźnienie w odzwierciedleniu odpowiednich uprawnień w latarni morskiej. | Ten problem zostanie rozwiązany w ciągu 30 minut. Nie są wymagane żadne dodatkowe kroki. |

## <a name="granular-delegated-admin-permissionsgdap"></a>Szczegółowe, delegowane uprawnienia administratora (GDAP)

> [!NOTE]
> GDAP jest obecnie w [wersji Technical Preview (publiczna](/partner-center/announcements/2022-february#6) wersja Zapoznawcza), aby umożliwić partnerom przypisywanie szczegółowych uprawnień przed ogólnym dostępem do usługi GDAP.

| Problem | Opis | Rozwiązanie |
| ---------------- | ---------------- | ---------------- |
| **Różne problemy z uprawnieniami GDAP w latarni morskiej** | <ul><li>Administratorzy zabezpieczeń GDAP nie mogą wyświetlać ryzykownych użytkowników, odrzucać zagrożeń ani potwierdzać naruszonych użytkowników.</li><li>Czytniki zabezpieczeń GDAP nie mogą wyświetlać ryzykownych użytkowników.</li><li>Administratorzy globalni GDAP widzą komunikat o błędzie podczas próby wyświetlenia kondycji usługi.</li></ul> | Przed ogólną dostępnością GDAP obejściem tego problemu jest przypisanie użytkownikowi roli GDAP administratora globalnego lub roli DAP agenta administracyjnego. Aby uzyskać instrukcje dotyczące przypisywania roli GDAP administratora globalnego, zobacz Uzyskiwanie szczegółowych uprawnień administratora w celu zarządzania [usługą klienta](/partner-center/gdap-obtain-admin-permissions-to-manage-customer). Aby uzyskać instrukcje na temat przypisywania roli administratora w programie agent daP, zobacz [Przypisywanie ról i uprawnień użytkownikom](/partner-center/permissions-overview). Aby uzyskać listę akcji, które wymagają pewnych ról Azure Active Directory w dzierżawie partnera, zobacz Konfigurowanie zabezpieczeń Microsoft 365 Lighthouse [portalu](/microsoft-365/lighthouse/m365-lighthouse-configure-portal-security).

## <a name="localization"></a>Lokalizacja

| Problem | Opis | Rozwiązanie |
| ---------------- | ---------------- | ---------------- |
| **Problemy z tłumaczeniami** | Użytkownicy mogą doświadczać problemów z tłumaczeniem języków, gdy język przeglądarki lub ich wybór języka w latarnice morski jest niczym innym niż angielski. | Aby zminimalizować problemy z tłumaczeniami w latarni morskiej, upewnij się, że wybór języka przeglądarki jest taki, jak w przypadku ustawienia języka w portalu Lighthouse. Aby zmienić wybór języka w latarni morskiej, zaloguj się do lighthouse i wybierz ikonę koła zębatego u góry strony, aby otworzyć stronę ustawień portalu, wybierz pozycję Język **+ region**, a następnie wybierz odpowiednie formaty językowe i regionalne. |

## <a name="related-content"></a>Zawartość pokrewna

[Microsoft 365 Lighthouse faq](m365-lighthouse-faq.yml) (artykuł)\
[Rozwiązywanie problemów i komunikatów o błędach w programie Microsoft 365 Lighthouse](m365-lighthouse-troubleshoot.md) (artykuł)\
[Uzyskiwanie pomocy technicznej dotyczącej Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md) (artykuł)