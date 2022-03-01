---
title: Migrowanie do usługi Microsoft Defender Office 365 etap 1. Przygotowywanie
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: migrationguides
description: Wymagania wstępne dotyczące migrowania z usługi lub urządzenia ochrony innej firmy do programu Microsoft Defender w Office 365 ochrony.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f8a35fa7e8ac469a87861d25f45e7078eb4be940
ms.sourcegitcommit: 23a90ed17cddf3b0db8d4084c8424f0fabd7b1de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/17/2022
ms.locfileid: "63014843"
---
# <a name="migrate-to-microsoft-defender-for-office-365---phase-1-prepare"></a>Migrowanie do usługi Microsoft Defender dla Office 365 — Etap 1. Przygotowywanie

**Dotyczy**
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)

<br>

|![Etap 1. Przygotowanie.](../../media/phase-diagrams/prepare.png) <br> Etap 1. Przygotowywanie|[![Etap 2. Konfigurowanie](../../media/phase-diagrams/setup.png)](migrate-to-defender-for-office-365-setup.md) <br> [Etap 2. Konfigurowanie](migrate-to-defender-for-office-365-setup.md)|[![Etap 3. Wniesienie](../../media/phase-diagrams/onboard.png)](migrate-to-defender-for-office-365-onboard.md) <br> [Etap 3. Wniesienie](migrate-to-defender-for-office-365-onboard.md)|
|---|---|---|
|*Jesteś tutaj!*|||

Etap **1: Przygotowywanie** migracji do programu **[Microsoft Defender](migrate-to-defender-for-office-365.md#the-migration-process)** dla Office 365! Ten etap migracji obejmuje następujące kroki. Przed rozpoczęciem jakichkolwiek zmian należy zase spisać ustawienia w istniejącej usłudze ochrony. W przeciwnym razie możesz wykonać pozostałe kroki w dowolnej kolejności:

1. [Inwentaryzacja ustawień w istniejącej usłudze ochrony](#inventory-the-settings-at-your-existing-protection-service)
2. [Sprawdzanie istniejącej konfiguracji ochrony w programie Microsoft 365](#check-your-existing-protection-configuration-in-microsoft-365)
3. [Sprawdzanie konfiguracji routingu poczty](#check-your-mail-routing-configuration)
4. [Przenoszenie funkcji modyfikujących wiadomości do Microsoft 365](#move-features-that-modify-messages-into-microsoft-365)
5. [Definiowanie spamu i zbiorczego obsługi użytkowników](#define-spam-and-bulk-user-experiences)
6. [Identyfikowanie i wyznaczanie kont priorytetowych](#identify-and-designate-priority-accounts)

## <a name="inventory-the-settings-at-your-existing-protection-service"></a>Inwentaryzacja ustawień w istniejącej usłudze ochrony

Dobrym pomysłem jest pełny spis ustawień, reguł, wyjątków i tym podobnej od istniejącej usługi ochrony, ponieważ prawdopodobnie nie będziesz mieć dostępu do informacji po anulowaniu subskrypcji.

**Jednak nie należy automatycznie ani arbitrowo ponownie tworzyć wszystkich istniejących dostosowań w programie Defender dla systemu Office 365.** W najlepszym razie możesz wprowadzić ustawienia, które nie są już wymagane, istotne ani funkcjonalne. Co gorsza, niektóre z poprzednich dostosowań w rzeczywistości mogą spowodować problemy z zabezpieczeniami w programie Defender dla Office 365.

Testowanie i obserwacja natywnych możliwości i zachowania usługi Defender dla systemu Office 365 ostatecznie będzie określać konieczne zastąpienia i ustawienia. Pomocne może okazać się podzielnie ustawień istniejącej usługi ochrony na następujące kategorie:

- **Filtrowanie połączenia lub zawartości**: Prawdopodobnie nie będziesz potrzebować większości tych dostosowań w programie Defender dla systemu Office 365.
- **Routing biznesowy**. Większość dostosowań, które należy ponownie utworzyć, prawdopodobnie znajdzie się w tej kategorii. Na przykład możesz ponownie utworzyć te ustawienia w programie Microsoft 365, Exchange reguł przepływu poczty e-mail (nazywanych także regułami transportu), łączników i wyjątków przed fałszerwną analizą.

Zamiast przesuwać stare ustawienia na Microsoft 365, zalecamy podejście kaskadowe, które obejmuje fazę pilotażową z stale rosnącym członkostwem użytkowników i dostosowywaniem na podstawie obserwacji opartym na równoważeniu kwestii zabezpieczeń z potrzebami biznesowymi organizacji.

## <a name="check-your-existing-protection-configuration-in-microsoft-365"></a>Sprawdzanie istniejącej konfiguracji ochrony w programie Microsoft 365

Jak już wspomniano, nie można całkowicie wyłączyć wszystkich funkcji ochrony poczty dostarczanej do usługi Microsoft 365, nawet jeśli korzystasz z usługi ochrony innej firmy. Dlatego nie jest niczym niezwykłym, Microsoft 365 musi mieć skonfigurowane co najmniej niektóre funkcje ochrony poczty e-mail. Przykład:

- W przeszłości nie korzystano z usługi ochrony innych firm z usługą Microsoft 365. Być może korzystano i skonfigurowano pewne funkcje ochrony w programie Microsoft 365 które są obecnie ignorowane. Jednak te ustawienia mogą zostać wprowadzone w celu włączenia funkcji ochrony w programie Microsoft 365.
- Możesz korzystać z miejsca pobytu w celu ochrony Microsoft 365 wynikach fałszywie dodatnich (dobra poczta oznaczona jako zła) lub wyników fałszywie ujemnych (zbędna poczta jest dozwolona), dzięki temu zostały one wprowadzone za pośrednictwem istniejącej usługi ochrony.

Przejrzyj istniejące funkcje ochrony w programie Microsoft 365 i rozważ usunięcie lub uproszczenie ustawień, które nie są już wymagane. Ustawienie reguły lub zasad, które było wymagane kilka lat temu, może stanowić zagrożenie dla organizacji i utworzyć niezamierzone przerwy w ochronie.

## <a name="check-your-mail-routing-configuration"></a>Sprawdzanie konfiguracji routingu poczty

- Jeśli używasz dowolnego rodzaju złożonego routingu (na przykład scentralizowanego transportu [poczty), rozważ](/exchange/transport-options) uproszczenie routingu i dokładne dokumentowanie go. Przeskoki zewnętrzne, zwłaszcza Microsoft 365 wiadomość, mogą utrudniać konfigurację i rozwiązywanie problemów.

- Wychodzący i przekazujący przepływ poczty e-mail nie należy do zakresu tego artykułu. Pamiętaj jednak, że może być konieczne wykonać co najmniej jedną z następujących czynności:
  - Upewnij się, że wszystkie domeny, których używasz do wysyłania wiadomości e-mail, mają odpowiednie rekordy SPF. Aby uzyskać więcej informacji, zobacz [Konfigurowanie spf w celu zapobiegania spoofingowi](set-up-spf-in-office-365-to-help-prevent-spoofing.md).
  - Zdecydowanie zalecamy konfigurowanie logowania się do programu DKIM w Microsoft 365. Aby uzyskać więcej informacji, zobacz [Używanie funkcji DKIM do sprawdzania poprawności wychodzących wiadomości e-mail](use-dkim-to-validate-outbound-email.md).
  - Jeśli poczta nie jest przekierowywana bezpośrednio Microsoft 365, musisz zmienić ten routing, usuwając lub zmieniając łącznik ruchu wychodzącego.

- Przekazywanie Microsoft 365 e-mail z lokalnych serwerów poczty e-mail za pomocą Microsoft 365 samo w sobie może być złożonym projektem. Prostym przykładem jest niewielka liczba aplikacji lub urządzeń, które wysyłają większość ich wiadomości do adresatów wewnętrznych i nie są używane do wysyłki masowej. Szczegółowe [informacje można znaleźć](/exchange/mail-flow-best-practices/how-to-set-up-a-multifunction-device-or-application-to-send-email-using-microsoft-365-or-office-365) w tym przewodniku. Bardziej rozbudowane środowiska muszą być bardziej przemyślane. Marketingowe wiadomości e-mail i wiadomości, które mogą być widziane przez adresatów jako spam, są niedozwolone.

- Funkcja Defender Office 365 nie ma funkcji agregowania raportów DMARC. Odwiedź katalog [Microsoft Intelligent Security Association (MISA),](https://www.microsoft.com/misapartnercatalog) aby wyświetlić dostawców zewnętrznych, którzy oferują raporty DMARC dla Microsoft 365.

## <a name="move-features-that-modify-messages-into-microsoft-365"></a>Przenoszenie funkcji modyfikujących wiadomości do Microsoft 365

Musisz przenieść wszelkie dostosowania lub funkcje modyfikujące wiadomości w jakikolwiek sposób Microsoft 365. Na przykład istniejąca usługa ochrony dodaje tag **Zewnętrzny** do tematu lub do treści wiadomości od zewnętrznych nadawców. Dowolna funkcja zawijania linków będzie również powodować problemy w przypadku niektórych wiadomości. Jeśli używasz obecnie takiej funkcji, priorytetowo powinien zostać wyeks tym związane z Sejf linków w celu zminimalizowania problemów.

Jeśli nie wyłączysz funkcji modyfikowania wiadomości w istniejącej usłudze ochrony, możesz oczekiwać następujących negatywnych wyników dla Microsoft 365:

- W programie DKIM zostanie przerwiena. Nie wszyscy nadawcy korzystają z DKIM, ale w przypadku tych, które nie przejdą uwierzytelniania.
- [Sfałszowana inteligencja](anti-spoofing-protection.md) i krok dostosowywania w dalszej części tego przewodnika nie będą działać poprawnie.
- Prawdopodobnie otrzymasz dużą liczbę wyników fałszywie dodatnich (dobra wiadomość oznaczona jako zła).

Aby ponownie utworzyć identyfikację zewnętrznego Microsoft 365 w programie Microsoft 365, dostępne są następujące opcje:

- Funkcja [Outlook out nadawcy](https://techcommunity.microsoft.com/t5/exchange-team-blog/native-external-sender-callouts-on-email-in-outlook/ba-p/2250098) zewnętrznego wraz z pierwszymi poradami [dotyczącymi bezpieczeństwa w kontakcie](set-up-anti-phishing-policies.md#first-contact-safety-tip).
- Reguły przepływu poczty (nazywane także regułami transportu). Aby uzyskać więcej informacji, zobacz Zastrzeżenia, podpisy, stopki lub nagłówki wiadomości dla całej [organizacji w programie Exchange Online](/exchange/security-and-compliance/mail-flow-rules/disclaimers-signatures-footers-or-headers).

Firma Microsoft współpracuje z branżą w celu obsługi standardu ARC (Authenticated Received Chain) w niedalekiej przyszłości. Jeśli chcesz pozostawić włączone funkcje modyfikowania wiadomości u bieżącego dostawcy bramy poczty, zalecamy skontaktowanie się z nim w sprawie planów obsługi tego standardu.

## <a name="account-for-any-active-phishing-simulations"></a>Konto dla dowolnej aktywnej symulacyjnej próby wyłudzania informacji

Jeśli masz aktywne przykłady wyłudzania informacji od innych firm, musisz zapobiec zidentyfikowaniu wiadomości, linków i załączników jako prób wyłudzenia informacji przez usługę Defender for Office 365. Aby uzyskać więcej informacji, zobacz Konfigurowanie przykładów wyłudzania informacji innych firm [w zaawansowanych zasadach dostarczania](configure-advanced-delivery.md#use-the-microsoft-365-defender-portal-to-configure-third-party-phishing-simulations-in-the-advanced-delivery-policy).

## <a name="define-spam-and-bulk-user-experiences"></a>Definiowanie spamu i zbiorczego obsługi użytkowników

- **Kwarantanna a dostarczanie do folderu Wiadomości-śmieci**: naturalną i zalecaną odpowiedzią na złośliwe i zdecydowanie ryzykowne wiadomości jest kwarantanna wiadomości. Jak jednak użytkownicy mają poradzić sobie z mniej szkodliwymi wiadomościami, takimi jak spam i poczta zbiorcza (znana również jako *szara poczta*). Czy te typy wiadomości powinny być dostarczane do folderów wiadomości-śmieci użytkowników?

  W naszych standardowych ustawieniach zabezpieczeń te mniej ryzykowne typy wiadomości są na ogół wysyłane do folderu Wiadomości-śmieci. Takie działanie jest podobne do wielu ofert poczty e-mail dla klientów indywidualnych, w których użytkownicy mogą sprawdzić, czy w folderze wiadomości-śmieci nie ma brakujących wiadomości, i sami mogą pomóc w pracy z tymi wiadomościami. Jeśli użytkownik celowo załozył konto w biuletynie lub wiadomości marketingowej, może anulować subskrypcję lub zablokować nadawcę dla swojej skrzynki pocztowej.

  Jednak wielu użytkowników w przedsiębiorstwach często używa niewielkiej poczty w folderze Wiadomości-śmieci (jeśli takie wiadomości istnieją). Zamiast tego użytkownicy w przedsiębiorstwie sprawdzają w kwarantannie brakujące wiadomości. Kwarantanna wprowadza problemy dotyczące powiadomień kwarantanny, częstotliwości powiadomień oraz uprawnień wymaganych do wyświetlania i udostępniania wiadomości.

  - Podziały kluczy domen (DKIM, Domain Keys Identified Mail).
  - [Spoof intelligence](anti-spoofing-protection.md) will not work properly.
  - Prawdopodobnie otrzymasz dużą liczbę wyników fałszywie dodatnich (dobra wiadomość oznaczona jako zła).

  Ostatecznie decyzja należy do Ciebie, jeśli chcesz uniemożliwić dostarczenie wiadomości e-mail do folderu Wiadomości-śmieci na rzecz dostarczania ich do kwarantanny. Jedno jest jednak pewne: jeśli środowisko programu Defender dla systemu Office 365 różni się od tego, do czego służą Twoi użytkownicy, musisz powiadomić ich i zapewnić podstawowe szkolenie. Wdaj się w nauce z programu pilotażowego i upewnij się, że użytkownicy są przygotowani na nowe zachowanie w celu dostarczania wiadomości e-mail.

- **Wanted bulk mail vs. unwanted bulk mail**: Many protection systems allow users to allow or block bulk email for themselves. Te ustawienia nie są łatwo migrowane do usługi Microsoft 365, dlatego warto rozważyć współpracę z pracownikami sieci VI i ich pracownikami w celu ponownego odtworzenia istniejących konfiguracji w Microsoft 365.

  Obecnie Microsoft 365 poczty masowej (na przykład biuletyny) jako bezpieczne w zależności od źródła wiadomości. Wiadomości z tych "bezpiecznych" źródeł nie są obecnie oznaczane jako zbiorcze (poziom skarg zbiorczych wynosi 0 lub 1), więc globalnie trudno jest zablokować pocztę z tych źródeł. W przypadku większości użytkowników rozwiązaniem jest poprosienie ich o indywidualne anulowanie subskrypcji tych wiadomości zbiorczych Outlook zablokowanie nadawcy. Jednak niektórym użytkownikom nie spodoba się blokowanie lub subskrybowanie samych wiadomości zbiorczych.

  Reguły przepływu poczty e-mail, które filtrują zbiorcze wiadomości e-mail, mogą być przydatne, gdy użytkownicy programu VIP nie chcą zarządzać tym samym. Aby uzyskać więcej informacji, zobacz Filtrowanie zbiorczej poczty [e-mail za pomocą reguł przepływu poczty e-mail](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-filter-bulk-mail).

## <a name="identify-and-designate-priority-accounts"></a>Identyfikowanie i wyznaczanie kont priorytetowych

Jeśli ta funkcja jest dla Ciebie **dostępna, konta** priorytetowe  i tagi użytkownika mogą pomóc w zidentyfikowaniu ważnych użytkowników Microsoft 365 wyróżniania ich w raportach. Aby uzyskać więcej informacji, zobacz Tagi użytkowników w [programie Microsoft Defender Office 365](user-tags.md) i [Zarządzanie kontami o priorytecie i monitorowanie ich](/microsoft-365/admin/setup/priority-accounts).

## <a name="next-step"></a>Następny krok

**Gratulacje**! Ukończono etap **Przygotuj** migrację do [programu Microsoft Defender dla systemu Office 365](migrate-to-defender-for-office-365.md#the-migration-process)!

- Przejdź do [fazy 2. Konfigurowanie](migrate-to-defender-for-office-365-setup.md).
