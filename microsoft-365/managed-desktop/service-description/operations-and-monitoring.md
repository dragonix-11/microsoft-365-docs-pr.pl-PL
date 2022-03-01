---
title: Microsoft Managed Desktop i monitorowanie danych
description: KtoTo, co robi dla różnych procesów zmian
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
ms.openlocfilehash: 6b1771660cb25ccd9d23c97d1e3fcf6edd27feaa
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2022
ms.locfileid: "63014764"
---
# <a name="microsoft-managed-desktop-operations-and-monitoring"></a>Microsoft Managed Desktop i monitorowanie danych

<!-- Operations and monitoring: -->

## <a name="change-management"></a>Zarządzanie zmianami

W ofercie usługi odpowiedzialność za konserwację sprzętu i aktualizacje zabezpieczeń spoczywa na kliencie (usługodawca) zamiast na kliencie (Ty). Mimo to musisz jednak zagwarantować, że oprogramowanie inne niż firma Microsoft i niestandardowe będzie nadal działać zgodnie z oczekiwaniami po w związku z aktualizacją.

W przypadku produktów lokalnych twoja organizacja ponosi pełną odpowiedzialność za zarządzanie zmianą.

### <a name="balance-of-responsibility"></a>Saldo odpowiedzialności

| Odpowiedzialność | Microsoft Managed Desktop usługi | Microsoft 365 klienta | Lokalni klienci i serwery | Oprogramowanie niestandardowe i inne niż firma Microsoft
| ----- | ----- | ----- | ----- | ----- |
| Udostępnij nowe funkcje | Microsoft | Microsoft | Oba | Klient
| Testowanie nowych funkcji w celu zapewniania jakości |  Microsoft | Microsoft | Oba | Klient
| Komunikowanie się o nowych funkcjach | Oba | Oba | Oba | Klient
| Integracja niestandardowego oprogramowania | Oba | Oba | Klient | Klient
| Stosowanie aktualizacji zabezpieczeń | Microsoft | Microsoft | Klient | Klient
| Obsługa oprogramowania systemowego | Microsoft | Microsoft | Klient | Klient
| Pakiet do wdrożenia | Microsoft | Microsoft | Klient | Klient

### <a name="change-process-overview"></a>Omówienie procesu zmiany

Poniżej znajduje się podsumowanie tego, jak proces zmiany jest udostępniany firmie Microsoft i klientom:

| Scenariusz | Rola firmy Microsoft | Rola klienta |
| ----- | ----- | ----- |
| Przed zmianą | <ul><li>Ustaw oczekiwania na zmiany w usłudze.</li><li>Powiadamianie klientów z 5-dniowy wyprzedzeniem o zmianach, które wymagają działania administratora.</li><li>W przypadku zmian w sytuacjach awaryjnych zastosuj środki zaradcze przed powiadomieniem.</li></ul> | <ul><li>Zrozumienie, czego można oczekiwać w przypadku zmian i komunikacji.</li><li>Regularnie Microsoft Managed Desktop wiadomości w Centrum wiadomości.</li><li>Przegląd i aktualizacja wewnętrznych procesów zarządzania zmianami.</li><li>Zrozumienie i sprawdzenie zgodności z Microsoft Managed Desktop wymagań. </li><li>Potwierdzanie i zatwierdzanie, gdy jest to wymagane.</li></ul>
| Podczas zmiany | <ul><li>Rozsyłaj i wdrażaj comiesięczne aktualizacje zabezpieczeń i niezwiązywowe dla klientów Windows 10 i Office 365 klientów.</li><li>Monitoruj sygnały danych i obsługuj kolejki w celu ich wpływu.</li></ul> | <ul><li>Sprawdź centrum Microsoft Managed Desktop wiadomości i przejrzyj wszelkie dodatkowe informacje.</li><li>Jeśli to konieczne, należy podjąć wszelkie wymagane działania i przetestować aplikacje.</li><li>Jeśli wystąpił problem z przerwą/poprawą, utwórz zgłoszenie do pomocy technicznej.</li></ul> |
| Po zmianie | <ul><li>Zbieraj opinie klientów, aby ulepszyć przyszłe zmiany.</li><li>Monitoruj sygnały danych i obsługuj kolejki w celu ich wpływu.</li></ul> | <ul><li>We współpracy z osobami w organizacji zaadoptuj zmiany.</li><li>Przegląd procesów zarządzania zmianami i jego przyjęciami w celu uzyskania efektywnej wydajności.</li><li>W narzędziu do opiniowania administratorów możesz przekazać ogólną opinię i konkretną opinię.</li><li>Szkolenie użytkowników w celu świadczyć opinie na temat poszczególnych aplikacji za Centrum opinii o systemie Windows aplikacji i przycisku Uśmiech Office aplikacji.</li></ul> |

### <a name="change-types"></a>Zmienianie typów

Jest kilka typów zmian, które regularnie wprowadzamy w usłudze. Kanał komunikacji tych zmian i działań, za które odpowiadasz, różnią się.

Nie wszystkie zmiany mają ten sam wpływ na Twoich użytkowników lub wymagają działania. Niektóre są planowane, a inne są niezaplanowane. Na przykład aktualizacje niezwiązywają z zabezpieczeniami i aktualizacje zabezpieczeń nie są zazwyczaj planowane.

W zależności od typu zmiany kanał komunikacji może się różnić. W poniższej tabeli wymieniono typy zmian, których można oczekiwać w Microsoft Managed Desktop usługi.

|  | Funkcje | Aktualizacje niezwiązane z bezpieczeństwem | Bezpieczeństwo |
| ----- | ----- | ----- | ----- |
| **Typ zmiany** | <ul><li>Aktualizacje funkcji</li><li>Nowe funkcje lub aplikacje</li><li>Przestarzałe funkcje</li></ul> | Poprawki klientów dotyczące problemów | Aktualizacje zabezpieczeń |
**Wcześniejsze powiadomienie** | Powiadomienie o zmianach wymagających działania jest powiadomienia o pięciu dniach | Żadne takie zmiany nie są uwzględniane w comiesięcznej wersji | W comiesięcznej wersji nie są uwzględniane żadne zmiany |
**Kanał komunikacji** | <ul><li>Centrum wiadomości</li><li>Alert e-mail</li></ul> | <ul><li>Centrum wiadomości</li><li>Alert e-mail</li></ul> | <ul><li>Centrum wiadomości</li><li>Alert e-mail</li></ul> |
**Wymaga działania administratora globalnego** | Czasami | Rzadko | Rzadko |
**Typ akcji** | Zmień ustawienia | Komunikowanie zmian użytkownikom | Zmienianie ustawień administratora |
**Wymaga testów** | Sprawdzanie aplikacji biznesowych, w tym usług dostępu zdalnego | Czasami; testowanie poprawki pod względem procesów lub dostosowań | Rzadko |
**Przykłady zmian** | <ul><li>Aktualizacje funkcji: Portal administracyjnym IT upraszcza przesyłanie i przeglądanie zgłoszeń do pomocy technicznej</li><li>Nowe funkcje lub aplikacje: Semi-Annual aktualizacji Windows 10 funkcji</li></ul> | Poprawki na podstawie zgłoszonych przez klientów błędów |

## <a name="standard-operating-procedures"></a>Standardowe procedury operacyjne

Usługa Microsoft Managed Desktop jest zaimplementowana i obsługiwana przez firmę Microsoft w Twoim wystąpieniu chmury firmy Microsoft, w którym możesz prowadzić inne działania administracyjne. Firma Microsoft ponosi wyłączną odpowiedzialność za Microsoft Managed Desktop, konfiguracji i operacji.

W przypadku produktów lokalnych twoja organizacja ponosi pełną odpowiedzialność za zarządzanie konfiguracją, konfiguracją i działaniami operacyjnymi.

| Kategorie | Firma Microsoft | Klient |
| ----- | ----- | ----- |
| Sieć (serwer proxy, inspekcja pakietów, sieć VPN) | Porady i planowanie z klientami w celu zminimalizowania ryzyka dla użytkowników biznesowych. | <ul><li>Utwórz wniosek o pomoc techniczną z prośbą o informacje dotyczące planowanej zmiany konfiguracji. Dołącz szczegóły konfiguracji, zakres, oś czasu i inne istotne szczegóły do przejrzenia przez firmę Microsoft.</li><li>Zmiany należy stosować tylko w przypadku Microsoft Managed Desktop i zalecania operacji.</li></ul> |
Konta usług | <ul><li>Implementacja, bezpieczne przechowywanie poświadczeń i zarządzanie nimi.</li><li>Nieautoryzowany dostęp lub używanie tych poświadczeń należy przekazywać zespołowi ds. operacji zabezpieczeń.</li></ul> | <ul><li>Utwórz wniosek o pomoc techniczną z prośbą o informacje dotyczące planowanej zmiany konfiguracji. Dołącz szczegóły konfiguracji, zakres, oś czasu i inne istotne szczegóły do przejrzenia przez firmę Microsoft.</li><li>Zmiany należy stosować tylko w przypadku Microsoft Managed Desktop i zalecania operacji.</li><li>Nie przypisuj zasad, uwierzytelniania wieloskładnikowego, dostępu warunkowego ani wdrożenia aplikacji do kont Microsoft Managed Desktop usług.</li><li>Nie resetuj hasła ani nie używaj poświadczeń.</li><li>Otwórz wniosek o pomoc techniczną Sev C w celu Microsoft Managed Desktop podejrzanych działań w usłudze Intune lub dziennikach inspekcji platformy Azure, związanych z tymi kontami usługi.</li></ul>
| Grupy urządzeń | <li> Implementowanie i przypisywanie członkostwa na urządzeniach w Microsoft Managed Desktop grupy.</li><li>Użyj grup Microsoft Managed Desktop, aby zarządzać przypisywaniem i wydaniem konfiguracji i aktualizacji urządzeń.</li></ul> | <ul><li>Utwórz wniosek o pomoc techniczną z prośbą o informacje dotyczące planowanej zmiany konfiguracji. Dołącz szczegóły konfiguracji, zakres, oś czasu i inne istotne szczegóły do przejrzenia przez firmę Microsoft.</li><li>Zmiany należy stosować tylko w przypadku Microsoft Managed Desktop i zalecania operacji.</li><li>Urządzenia należy przypisywać tylko do Microsoft Managed Desktop, zgodnie z instrukcjami w tece [Przypisywanie urządzeń do grupy wdrażania](../working-with-managed-desktop/assign-deployment-group.md).</li><li>Za pomocą grup przypisuj certyfikaty firmowe tylko dla usług takich jak VPN, Windows Hello for Business, szyfrowanie poczty e-mail lub konfiguracja firmowego profilu wifi.</li><li>Jeśli istnieje współzawłasnie, jawnie wyklucz Microsoft Managed Desktop grupy podczas wdrażania Menedżer konfiguracji klienta.</li></ul>
| Policies (zasady) | <ul><li>Implementowanie zasad Microsoft Managed Desktop i zarządzanie nimi, które określają stan konfiguracji urządzeń w usłudze.</li><li> Wdrażaj aktualizacje w zasadach lub Windows, stopniowo za pomocą grup urządzeń.</li><li>Jawnie wykluczaj kierowanie docelowych Microsoft Managed Desktop grup.</li></ul> | <ul><li>Utwórz wniosek o pomoc techniczną z prośbą o informacje dotyczące planowanej zmiany konfiguracji. Dołącz szczegóły konfiguracji, zakres, oś czasu i inne istotne szczegóły do przejrzenia przez firmę Microsoft.</li><li>Zmiany należy stosować tylko w przypadku Microsoft Managed Desktop i zalecania operacji.</li><li>Nie edytuj ani nie przypisuj zasad Microsoft Managed Desktop do urządzeń lub użytkowników, których nie zarządza Microsoft Managed Desktop usługi.
Microsoft 365 Defender dla punktu końcowego.</li></ul> | Monitoruj i badaj urządzenia w ramach Microsoft Managed Desktop usługi. | <ul><li>Utwórz wniosek o pomoc techniczną z prośbą o informacje dotyczące planowanej zmiany konfiguracji. Dołącz szczegóły konfiguracji, zakres, oś czasu i inne istotne szczegóły do przejrzenia przez firmę Microsoft.</li><li>Zmiany należy stosować tylko w przypadku Microsoft Managed Desktop i zalecania operacji.</li></ul>
| Microsoft Store dla Firm | Konfigurowanie i obsługa profilu Windows rozwiązania Autopilot dla Microsoft Managed Desktop usługi. | <ul><li>Utwórz wniosek o pomoc techniczną z prośbą o informacje dotyczące planowanej zmiany konfiguracji. Dołącz szczegóły konfiguracji, zakres, oś czasu i inne istotne szczegóły do przejrzenia przez firmę Microsoft.</li><li>Zmiany należy stosować tylko w przypadku Microsoft Managed Desktop i zalecania operacji.</li><li>Nie modyfikuj konfiguracji profilu rozwiązania Microsoft Managed Desktop Windows Autopilot ani dodawaj/usuwaj przypisanych urządzeń.</li></ul>
| Certyfikaty | | <ul><li>Utwórz wniosek o pomoc techniczną 60 dni przed wygaśnięciem certyfikatu i poproś o informacje o planowanej zmianie konfiguracji. Dołącz szczegóły konfiguracji, zakres, oś czasu i inne istotne szczegóły do przejrzenia przez firmę Microsoft.</li><li>Zmiany należy stosować tylko w przypadku Microsoft Managed Desktop i zalecania operacji.</li><li>Zaktualizuj wszystkie certyfikaty wymagane do skonfigurowania profilów certyfikatów, profilów sieci VPN Wi-Fi profilów.</li></ul>|

## <a name="device-wipe-with-factory-reset"></a>Czyszczenie urządzenia z przywróceniem ustawień fabrycznych

Zespół Microsoft Managed Desktop może wykonać resetowanie ustawień fabrycznych dla urządzeń zarejestrowanych w usłudze, jeśli jest to wymagane. Resetowanie jest przydatne, gdy trzeba dać urządzenie inowi pracownikowi lub gdy pracownik odchodzi z firmy.

Istnieje kilka wymagań:

- Administrator globalny musi przesłać wniosek o pomoc techniczną.
- Dołącz nazwę komputera urządzenia do żądania.
- Konto użytkownika musi być w usłudze Azure AD, zanim zresetujemy urządzenie.

Zespół zarządzanych operacji na pulpicie:

- Sprawdź nazwę urządzenia w usłudze Intune.
- Wyślij na urządzenie polecenie resetowania ustawień fabrycznych.

> [!NOTE]
> Nie usuwaj konta użytkownika z usługi Azure AD przed zresetowaniu urządzenia. Jeśli użytkownika nie ma w usłudze Azure AD, usługa Intune nie może wysłać na urządzenie polecenia resetowania ustawień fabrycznych.

Urządzenie zostanie uruchomione w "out of box experience", a wszystkie preinstalowane aplikacje i ustawienia zostaną ponownie zastosowane. Użytkownik urządzenia musi ponownie podać informacje o konfiguracji wstępnej.

Po zresetowaniu urządzenia możesz je przekazać innej osobie w organizacji. Na urządzeniu nie będą dane ani dane przedsiębiorstwa poprzedniego użytkownika. Następny użytkownik przejdą przez ten sam proces, który poprzedni użytkownik zrobił z nowym Microsoft Managed Desktop urządzeniem.

BitLocker to kluczowy składnik zabezpieczeń danych w tym procesie. Dzięki szyfrowaniu BitLocker Microsoft Managed Desktop urządzeniach dane na dysku pozostają bezpieczne nawet po przywróceniu ustawień fabrycznych na urządzeniu. Żadne dane, które były na dysku, nie będą dostępne dla następnego użytkownika urządzenia. Aby uzyskać więcej informacji, zobacz [Omówienie funkcji BitLocker](/windows/security/information-protection/bitlocker/bitlocker-overview).

Aby uzyskać więcej informacji, zobacz [Resetowanie urządzenia do ustawień fabrycznych](/intune/remote-actions/devices-wipe#factory-reset-a-device).
