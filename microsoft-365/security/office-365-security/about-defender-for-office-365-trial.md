---
title: Informacje o programie Microsoft Defender dla Office 365 próbnej
f1.keywords: ''
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdo
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
ROBOTS: NOINDEX, NOFOLLOW
description: Administratorzy mogą dowiedzieć się więcej o trybie próbnym programu Microsoft Defender dla Office 365
ms.openlocfilehash: 3d8d873a3e89b0ae3302eca0ab7d7c471fd94449
ms.sourcegitcommit: 39838c1a77d4e23df56af74059fb95970223f718
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "62973814"
---
# <a name="about-the-microsoft-defender-for-office-365-trial"></a>Informacje o programie Microsoft Defender dla Office 365 próbnej

> [!IMPORTANT]
> Szybko rozpoczynaj pracę z naszym łatwym w użyciu podręcznikiem do obsługi wersji próbnej [programu Microsoft Defender dla systemu Office 365](trial-playbook-defender-for-office-365.md). Ten podręcznik pomoże Ci w jak najczęściej korzystać z bezpłatnej wersji próbnej, pokazując, jak chronić organizację za pomocą programu Microsoft Defender dla Office 365.

Usługa Microsoft Defender for Office 365 chroni organizację przed złośliwymi zagrożeniami, które mogą być wyświetlane za pomocą wiadomości e-mail, linków (adresów URL) i narzędzi do współpracy. Program Defender for Office 365 oferuje:

- **Zasady ochrony przed zagrożeniami**: Zdefiniuj zasady ochrony przed zagrożeniami, aby ustawić odpowiedni poziom ochrony dla organizacji.
- **Raporty**: Wyświetlaj raporty w czasie rzeczywistym, aby monitorować program Defender Office 365 wydajności w organizacji.
- **Możliwości analizy zagrożeń i reagowania** na nie: Używaj narzędzi wiodących do badania, zrozumienia, symulowania i zapobiegania zagrożeniam.
- **Funkcje automatycznego badania i reagowania**: Oszczędzaj czas i wysiłku podczas badań i ograniczania zagrożeń.

Wersja próbna programu Microsoft Defender Office 365 to prosty sposób na bezpłatne wypróbowanie możliwości usługi Defender dla systemu Office 365 Plan 2 po zaledwie kilku kliknięciach. Te funkcje wysokiego poziomu opisano w poniższej tabeli:

<br>

****

|Funkcja|Opis|
|---|---|
|[Ustawienia wyłączności w zasadach ochrony przed wyłudzaniem informacji](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)|Uzyskaj ochronę personifikacji użytkownika, ochronę personifikacji domeny, inteligencję skrzynek pocztowych i zaawansowane progi wyłudzania informacji.|
|[Sejf załączników](safe-attachments.md)|Przeprowadzaj inspekcje załączników wiadomości e-mail i innych plików w środowisku kontrolowanym detonacji, aby wychwytować nowe i złośliwe oprogramowanie.|
|[Bezpieczne linki](safe-links.md)|Przekonuj testy po kliknięciu, aby upewnić się, że adresy URL, które mogły zostać pomyślnie przeprowadzonej inspekcji wstępnej, nie zostały zrównane.|
|[Śledzenie zagrożeń](threat-trackers.md)<sup>\*</sup>|Widżety i widoki informacyjne identyfikują problemy z tożsamością, które mogą mieć wpływ na organizację.|
|[Eksplorator zagrożeń](threat-explorer.md)<sup>\*</sup>|Przeszukaj wiadomości e-mail w czasie rzeczywistym z informacjami o Office 365 e-mail.|
|[Zautomatyzowane badania i odpowiedzi (AIR)](office-365-air.md)<sup>\*</sup>|Automatycznie lokalizuj i reagozuj obiekty zagrożeń w przypadku wyzwolenia alertów.|
|[Szkolenie z symeny ataków](attack-simulation-training.md)<sup>\*</sup>|Szkolenie użytkowników w celu odpowiedniego identyfikowania ataków wyłudzających informacje i odpowiadania na nie.|
|[Widoki kampanii](campaigns.md)<sup>\*</sup>|Badanie i reagowanie na dużą skalę złośliwych wiadomości e-mail.|
|[Raporty z użyciem programu Defender Office 365 możliwości](view-reports-for-mdo.md)|Wyświetlaj raporty, w tym informacje na temat stanu ochrony przed zagrożeniami, ochrony przed zagrożeniami za pośrednictwem adresów URL, opóźnień poczty i nie tylko.|
|[Priorytetowa ochrona konta](/microsoft-365/admin/setup/priority-accounts)<sup>\*</sup>|Użytkownicy zidentyfikowani jako konta o priorytecie są tagowane w alertach, raportach i badaniach, aby się wyróżniali. W filtrach można także użyć tagu Priority (Priorytet).|
|

<sup>\*</sup>Ta funkcja jest dostępna wyłącznie w uchcie Defender Office 365 Plan 2.

## <a name="set-up-a-defender-for-office-365-trial"></a>Konfigurowanie usługi Defender dla Office 365 próbnej

Wersja próbna umożliwia organizacjom łatwe konfigurowanie i konfigurowanie programu Defender na Office 365 możliwości. Podczas instalacji zasady, które są przeznaczone wyłącznie dla usługi Defender dla usługi Office 365 (w szczególności załączniki Sejf wiadomości [e-mail](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) Sejf[, linki](safe-attachments.md) do wiadomości e-mail i wiadomości [Microsoft Teams](safe-links.md) oraz ochrona przed personifikacjami w zasadach ochrony przed wyłudzaniem informacji) są stosowane przy użyciu szablonu Standardowe w celu ustawienia wstępnie ustawionych zasad [zabezpieczeń.](preset-security-policies.md)

Domyślnie te zasady są zakresowane do wszystkich użytkowników w organizacji, ale podczas konfigurowania wersji próbnej lub po jej zakończeniu możesz zmienić przypisanie zasad do konkretnych użytkowników.

> [!NOTE]
> Istniejące zasady ochrony przed spamem są prawdopodobnie skonfigurowane pod akcją Przenieś wiadomość do folderu Wiadomości-śmieci, aby mieć pewność, że werdykt spamu jest zasadą ochrony przed spamem. Szablon Standardowy dla wstępnie ustawionych zasad zabezpieczeń używa akcji  Kwarantanna wiadomości w celu zabezpieczenia przed spamem o dużej pewności, a wstępnie ustawione zasady zabezpieczeń są zawsze stosowane przed zastosowaniem niestandardowych zasad ochrony przed spamem lub domyślnymi zasadami ochrony przed spamem. Aby uzyskać więcej informacji na temat ustawień domyślnych, standardowych i ścisłych, zobacz Zalecane ustawienia usług [EOP i Microsoft Defender w Office 365 zabezpieczeń](recommended-settings-for-eop-and-office365.md).

Inne obciążenia pracą są również dostępne w celu ochrony (na przykład załączniki Sejf załączników do SharePoint[, OneDrive oraz](mdo-for-spo-odb-and-teams.md) linków Microsoft Teams i Sejf dla obsługiwanych Office 365 [aplikacji](safe-links.md#safe-links-settings-for-office-365-apps).

Podczas konfigurowania wersji próbnej funkcje reakcji, które są dostępne wyłącznie w programie Defender dla programu Office 365 (plan 2), na przykład [AIR](office-365-air.md) i [Eksplorator](threat-explorer.md) zagrożeń, są również konfigurne dla całej organizacji. Określanie zakresu zasad nie jest wymagane.

## <a name="licensing"></a>Licencjonowanie

W ramach konfiguracji wersji próbnej program Defender for Office 365 jest automatycznie stosowany do organizacji. Licencje są bezpłatne przez pierwsze 90 dni.

Na karcie licencjonowania dla wersji próbnej są podane następujące informacje:

![Karta licencjonowania w programie Microsoft Defender dla Office 365 próbnej.](../../media/mdo-trial-licensing-card.png)

- **Sekcja Typ** użycia:
  - **Wersja** próbna: liczba wersji próbnej usługi Defender Office 365 licencji dostępnych do użycia.

    > [!NOTE]
    > W innych lokalizacjach może być dostępna wartość 300 dla liczby dostępnych licencji wersji próbnej. Ta wartość jest niepoprawna (chyba że organizacja ma dokładnie 300 użytkowników). Liczba dostępnych licencji wersji próbnych odpowiada rozmiarowi Twojej organizacji, a nie dowolnej wartości 300.

  - **Zapłacono**: liczba płatnych licencji Office 365 Defender (jeśli jest).

- **Sekcja** Użycia: Ilu Twoich użytkowników jest objętych zasadami dostępu do usługi Defender Office 365 użytkowników.
  - **Wykrywanie & odpowiedzi**: Całkowita liczba użytkowników uwzględnionych w następujących scenariuszach:
    - Podczas okresu próbnego zasady te są określone dla konkretnych użytkowników.
    - Masz niestandardowe ustawienia dotyczące konkretnych użytkowników.
  - **Pełna ochrona**: całkowita liczba użytkowników chronionych przez program Defender dla funkcji Office 365 Plan 2 (AIR, Eksplorator zagrożeń, szkolenia symulacyjne dotyczące ataków itp.).

## <a name="permissions"></a>Uprawnienia

Aby rozpocząć lub zakończyć wersję próbną, musisz być członkiem ról **administratora** globalnego lub **administratora** zabezpieczeń w programie Azure Active Directory. Aby uzyskać szczegółowe informacje, zobacz [Informacje o rolach administratorów](../../admin/add-users/about-admin-roles.md).

## <a name="additional-information"></a>Informacje dodatkowe

Po rozpoczęciu okresu próbnego może upłynieć do 2 godzin, aż zmiany i aktualizacje będą dostępne. Administratorzy muszą się wylogować i zalogować ponownie, aby zobaczyć zmiany.

## <a name="availability"></a>Dostępność

Wersja próbna usługi Defender for Office 365 jest stopniowo wprowadzana u istniejących klientów, którzy spełniają określone kryteria i nie mają istniejących licencji usługi Defender dla usługi Office 365 Plan 2 (uwzględnionych w ich subskrypcji lub jako dodatek).

## <a name="terms-and-conditions"></a>Warunki i postanowienia

Aby uzyskać więcej informacji, zobacz [Warunki Office 365 próbne usługi Microsoft Defender & próbnego](defender-for-office-365-trial-terms-and-conditions.md).

## <a name="frequently-asked-questions"></a>Często zadawane pytania

### <a name="q-how-do-i-extend-the-trial"></a>P: Jak przedłużyć okres próbny?

O: Zobacz [Przedłużanie okresu próbnego](/microsoft-365/commerce/try-or-buy-microsoft-365#extend-your-trial).

### <a name="q-what-happens-to-my-data-after-the-trial-expires"></a>P: Co się stanie z moimi danymi po wygaśnięciu wersji próbnej?

O: Gdy wersja próbna wygaśnie, przez 30 dni będziesz mieć dostęp do danych wersji próbnej (danych z funkcji usługi Defender dla usługi Office 365, których wcześniej nie masz). Po tym 30-dniowym okresie wszystkie zasady i dane, które były skojarzone z programem Defender for Office 365 próbnej, zostaną usunięte.

### <a name="q-how-many-times-can-i-use-the-defender-for-office-365-trial-in-my-organization"></a>P. Ile razy mogę używać programu Defender na Office 365 próbnej w mojej organizacji?

O: Maksymalnie 2 razy. Jeśli twoja pierwsza wersja próbna wygaśnie, musisz poczekać co najmniej 30 dni po dacie wygaśnięcia, zanim będzie można ponownie zarejestrować się w programie Defender Office 365 próbnym. Po drugiej próbie nie możesz zarejestrować się do innej wersji próbnej.

## <a name="learn-more-about-defender-for-office-365"></a>Dowiedz się więcej o uchcie programu Defender dla Office 365

Program Defender for Office 365 pomaga organizacjom w zabezpieczeniach przedsiębiorstwa, oferując im pełną gamę możliwości.

Więcej informacji na temat programu Defender dla Office 365 znajdziesz w tym [interakcyjny przewodniku](https://aka.ms/MS365D.InteractiveGuide).

![Microsoft Defender dla Office 365 diagram koncepcyjny.](../../media/microsoft-defender-for-office-365.png)

### <a name="prevention"></a>Zapobieganie

Zaawansowany stos filtrowania zapobiega rozmaitym atakom opartym na woluminie i celom, w tym biznesowym utracie poczty e-mail, wyłudzaniu poświadczeń, oprogramowaniu wymuszającemu okup i zaawansowanemu oprogramowaniu złośliwym.

- [Zasady ochrony przed wyłudzaniem informacji: Ustawienia wyłączności w programie Defender dla Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
- [Sejf załączników](safe-attachments.md)
- [Bezpieczne linki](safe-links.md)

### <a name="detection"></a>Wykrywanie

Wiodąca w branży AI wykrywa złośliwą i podejrzaną zawartość oraz skoreluje wzorce ataków, aby zidentyfikować kampanie mające na celu ochronę przed złośliwymi reklamami.

- [Widoki kampanii w programie Microsoft Defender dla Office 365](campaigns.md)

### <a name="investigation-and-hunting"></a>Badania i łowiec

Zaawansowane środowisko pomaga identyfikować, priorytetyzować i badać zagrożenia, dzięki zaawansowanym możliwościom wyszukiwania w celu śledzenia ataków na Office 365.

- [Wykrywanie w Eksploratorze zagrożeń i w czasie rzeczywistym](threat-explorer.md)
- [Raporty w czasie rzeczywistym w programie Defender dla Office 365](view-reports-for-mdo.md)
- [Śledzenie zagrożeń — nowe i godne uwagi](threat-trackers.md)
- Integracja [z Microsoft 365 Defender](../defender/microsoft-365-defender.md)

### <a name="response-and-remediation"></a>Odpowiedzi i działania naprawcze

Rozbudowane funkcje reagowania na incydenty i automatyzacji zwiększaj skuteczność i wydajność Twojego zespołu zabezpieczeń.

- [Zautomatyzowane badania i odpowiedzi (AIR) w programie Microsoft Defender dla Office 365](office-365-air.md)

### <a name="awareness-and-training"></a>Świadomość i szkolenia

Rozbudowane funkcje symulacyjne i szkoleniowe oraz zintegrowane środowisko w aplikacjach klienckich, które rozbudowuje świadomość użytkowników.

- [Wprowadzenie do korzystania ze szkolenia symulacyjnego w zakresie ataków](attack-simulation-training-get-started.md)

### <a name="security-posture"></a>Postawa zabezpieczeń

Zalecane szablony i szczegółowe informacje o konfiguracji ułatwiają klientom uzyskiwanie i bezpieczeństwo.

- [Wstępnie ustawione zasady zabezpieczeń w usługach EOP i Microsoft Defender dla systemu Office 365](preset-security-policies.md)
- [Analizator konfiguracji do zasad ochrony w usługach EOP i Microsoft Defender for Office 365](configuration-analyzer-for-security-policies.md).

## <a name="give-feedback"></a>Opinie

Twoja opinia pomoże nam lepiej chronić Twoje środowisko przed zaawansowanymi atakami. Podziel się swoimi doświadczeniami i zbędną możliwościami produktu i wynikami wersji próbnej.
