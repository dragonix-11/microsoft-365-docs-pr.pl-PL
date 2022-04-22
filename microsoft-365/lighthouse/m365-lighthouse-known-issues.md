---
title: Znane problemy z Microsoft 365 Lighthouse
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
- M365-Lighthous
search.appverid: MET150
description: W przypadku dostawców usług zarządzanych korzystających z Microsoft 365 Lighthouse zobacz listę znanych problemów z usługą Lighthouse według obszaru funkcji.
ms.openlocfilehash: aa3b5980b60e966b4edfbac4a6e8d706c399e943
ms.sourcegitcommit: 339d2c2ffea06726f69429f73c1113c649f37b18
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2022
ms.locfileid: "65022784"
---
# <a name="known-issues-with-microsoft-365-lighthouse"></a>Znane problemy z Microsoft 365 Lighthouse

W tym artykule wymieniono znane problemy dotyczące Microsoft 365 Lighthouse według obszaru funkcji. Aby uzyskać więcej informacji na temat usługi Lighthouse, zobacz [Omówienie Microsoft 365 Lighthouse](m365-lighthouse-overview.md).

## <a name="users"></a>Użytkownicy

| Problem | Opis | Rozwiązanie |
| ---------------- | ---------------- | ---------------- |
| **Agent pomocy technicznej nie może zresetować hasła użytkownika** | Technicy dostawcy usług zarządzanych (MSP), którzy są członkami grupy Agent pomocy technicznej, nie mogą zresetować haseł dla użytkowników w dzierżawach klientów. Podczas próby zresetowania hasła użytkownika otrzymuje następujący komunikat o błędzie: "Nie masz do tego uprawnień. [Dowiedz się więcej](m365-lighthouse-configure-portal-security.md)" | Aby obejść problem z uprawnieniami, agenci pomocy technicznej powinni zresetować hasła przy użyciu Centrum administracyjne platformy Microsoft 365 lub Azure Active Directory. |

## <a name="devices"></a>Urządzeń

| Problem | Opis | Rozwiązanie |
| ---------------- | ---------------- | ---------------- |
| **Zostaną wyświetlone usunięte zasady** | Po usunięciu zasad zgodności urządzeń z Intune będzie ona tymczasowo nadal widoczna w usłudze Lighthouse. Jeśli technicy MSP spróbują wykonać porównanie zasad, które obejmuje usunięte zasady, technicy otrzymają następujący błąd: "Wystąpił problem. Odśwież stronę i spróbuj ponownie." | Aby rozwiązać ten problem, wyczyść usunięte zasady z porównania zasad i porównaj tylko istniejące zasady. |

## <a name="threat-management"></a>Zarządzanie zagrożeniami

| Problem | Opis | Rozwiązanie |
| ---------------- | ---------------- | ---------------- |
| **Brak nazwy zagrożenia** | Gdy technicy MSP wyświetlają listę zagrożeń na stronie Zarządzanie zagrożeniami, w niektórych zagrożeniach może brakować nazwy zagrożenia. Dzieje się tak, gdy urządzenie, na które wykryto zagrożenie, zostało niedawno usunięte z Intune. | Problem zostanie rozwiązany w ciągu 48 godzin. Nie są wymagane żadne dodatkowe kroki. |

## <a name="baselines"></a>Podstaw

| Problem | Opis | Rozwiązanie |
| ---------------- | ---------------- | ---------------- |
| **Ustawienia powodujące konflikt podczas porównywania kroków wdrażania bloku starszego uwierzytelniania i uwierzytelniania wieloskładnikowego** | Jeśli dzierżawa klienta wdrożyła blokowe starsze uwierzytelnianie i jeden z kroków wdrażania uwierzytelniania wieloskładnikowego, test porównawczy błędnie opisze te ustawienia jako powodujące konflikt. | Obejście nie jest wymagane. Ustawienia w rzeczywistości nie powodują konfliktu, a użytkownicy w dzierżawie klienta nie mają wpływu. |

## <a name="windows-365"></a>Windows 365

| Problem | Opis | Rozwiązanie |
| ---------------- | ---------------- | ---------------- |
| **Błąd ponownej aprowizacji** | Technicy MSP otrzymują komunikat o błędzie "Nie masz uprawnień do tego" podczas próby ponowienia aprowizowania komputera w chmurze. | Aby obejść ten problem, zaloguj się do dzierżawy klienta, a następnie ponownie zaaprowizuj komputery w chmurze z centrum administracyjnego rozwiązania Microsoft Endpoint Manger. Aby uzyskać instrukcje, zobacz [Reprovision a Cloud PC (Ponowne aprowizowanie komputera w chmurze](/windows-365/enterprise/reprovision-cloud-pc)). |

## <a name="audit-logs"></a>Dzienniki inspekcji


| Problem | Opis | Rozwiązanie |
|--|--|--|
| **Akcje dezaktywowania i ponownego aktywowania nie są wyświetlane w dziennikach inspekcji** | Następujące działania nie są obecnie zgłaszane na stronie Dzienniki inspekcji w aplikacji Lighthouse: <ul><li>Nazwa: offboardTenant Action: Inactivate a customer (Nazwa: offboardTenant \| Action: Inactivate a customer)</li> <li>Nazwa: resetTenantOnboardingStatus \| Action: Reaktywny klient</li></ul> | Nie ma obejścia, ale pracujemy nad poprawką. Te działania będą wyświetlane w dziennikach inspekcji po wdrożeniu poprawki w usłudze. |
| **Filtr nie pokazuje wszystkich użytkowników** | Gdy technicy MSP próbują filtrować przy użyciu opcji **Inicjowane przez**, lista wszystkich nazw głównych użytkowników (UPN) — odpowiadających identyfikatorom poczty e-mail techników, którzy zainicjowali akcje generujące dzienniki inspekcji — nie jest w pełni wyświetlana w filtrze.<br><br>Pamiętaj, że same dzienniki inspekcji zostaną w pełni wyświetlone. Ma to wpływ tylko na możliwość ich filtrowania przy użyciu funkcji **Inicjowane przez** . | Nie ma obejścia, ale pracujemy nad poprawką. Filtr powróci do oczekiwanego zachowania — wyświetlając pełną listę nazw UPN do filtrowania według — po wdrożeniu poprawki w usłudze. |

## <a name="delegated-admin-privileges-dap"></a>Delegowane uprawnienia administratora (DAP)

| Problem | Opis | Rozwiązanie |
| ---------------- | ---------------- | ---------------- |
| **Opóźnienie uprawnień podczas zmiany ról języka DAP** | Jeśli technik MSP zostanie dodany lub usunięty z grupy agenta administracyjnego lub agenta pomocy technicznej, może wystąpić opóźnienie w odzwierciedlaniu odpowiednich uprawnień w usłudze Lighthouse. | Problem zostanie rozwiązany w ciągu 30 minut. Nie są wymagane żadne dodatkowe kroki. |

## <a name="granular-delegated-admin-privileges-gdap"></a>Szczegółowe uprawnienia administratora delegowanego (GDAP)

> [!NOTE]
> Protokół GDAP jest obecnie w [wersji technical preview](/partner-center/announcements/2022-february#6) (publiczna wersja zapoznawcza), aby umożliwić partnerom przypisywanie szczegółowych uprawnień przed ogólnym udostępnieniem protokołu GDAP.

Obecnie dap jest wymagany do dołączenia klientów do lighthouse. Zalecamy również ustanowienie protokołu GDAP z klientami, aby umożliwić bezpieczniejszy dostęp delegowany. Chociaż dap i GDAP współistnieją, GDAP będzie mieć pierwszeństwo dla klientów, gdzie oba modele są w miejscu. Wkrótce klienci z zaledwie GDAP (i bez dap) będą mogli dołączyć do lighthouse.<br><br>

| Problem | Opis | Rozwiązanie |
| ---------------- | ---------------- | ---------------- |
| **Różne problemy z uprawnieniami GDAP w usłudze Lighthouse** | Niektóre role GDAP same w sobie nie zapewniają takiego samego poziomu dostępu do danych klientów w aplikacji Lighthouse, jak w środowisku jednej dzierżawy. Jeśli którakolwiek z następujących ról zostanie przypisana indywidualnie (nie jest to w połączeniu z innymi rolami GDAP) do techników MSP, mogą wystąpić błędy, w tym:<ul><li>Administratorzy zabezpieczeń GDAP nie mogą wyświetlać ryzykownych użytkowników, odrzucać ryzyka ani potwierdzać naruszeń zabezpieczeń użytkowników w usłudze Lighthouse.</li><li>Czytelnicy zabezpieczeń GDAP nie mogą wyświetlać ryzykownych użytkowników w usłudze Lighthouse.</li><li>Administratorzy globalni GDAP widzą komunikat o błędzie podczas próby wyświetlenia kondycji usługi w usłudze Lighthouse.</li><li>Administratorzy globalni GDAP mają problemy z wdrażaniem kroków planu wdrożenia w usłudze Lighthouse.</li></ul> | Obejście polega na przypisaniu kombinacji ról GDAP do techników MSP w oparciu o poziom dostępu do danych klientów, których potrzebują. Aby uzyskać listę zalecanych ról GDAP do korzystania z usługi Lighthouse, zobacz [Omówienie uprawnień w Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md).<br><br>W przypadku problemów, w których nawet uprawnienia administratora globalnego GDAP nie zezwalają na użycie funkcji w aplikacji Lighthouse, obejście polega na uzyskaniu dostępu do odpowiedniego centrum administracyjnego z dzierżawy klienta w celu zarządzania klientem (na przykład dostępu do Centrum administracyjne platformy Microsoft 365 z dzierżawy klienta w celu sprawdzenia kondycji usługi). Aby uzyskać instrukcje dotyczące modyfikowania relacji GDAP, zobacz [Uzyskiwanie szczegółowych uprawnień administratora do zarządzania usługą klienta — Centrum partnerskie](/partner-center/gdap-obtain-admin-permissions-to-manage-customer). |

## <a name="localization"></a>Lokalizacji

| Problem | Opis | Rozwiązanie |
| ---------------- | ---------------- | ---------------- |
| **Problemy z tłumaczeniem** | Użytkownicy mogą napotkać problemy z tłumaczeniem języka, gdy język przeglądarki lub wybór języka w aplikacji Lighthouse to coś innego niż angielski. | Aby zminimalizować problemy z tłumaczeniem w aplikacji Lighthouse, upewnij się, że wybór języka przeglądarki jest zgodny z ustawieniem języka w portalu lighthouse. Aby zmienić wybór języka w lighthouse, zaloguj się do lighthouse i wybierz ikonę koła zębatego w górnej części strony, aby otworzyć stronę ustawienia portalu, wybierz pozycję **Język i region**, a następnie wybierz odpowiedni język i formaty regionalne. |

## <a name="related-content"></a>Zawartość pokrewna

[Microsoft 365 Lighthouse często zadawane pytania](m365-lighthouse-faq.yml) (artykuł)\
[Rozwiązywanie problemów i komunikatów o błędach w Microsoft 365 Lighthouse](m365-lighthouse-troubleshoot.md) (artykuł)\
[Uzyskiwanie pomocy i obsługi technicznej dla Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md) (artykuł)
