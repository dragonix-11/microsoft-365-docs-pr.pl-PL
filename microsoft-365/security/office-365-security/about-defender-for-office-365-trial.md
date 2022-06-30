---
title: Informacje o wersji próbnej Ochrona usługi Office 365 w usłudze Microsoft Defender
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
description: Administratorzy mogą dowiedzieć się więcej o trybie próbnym Ochrona usługi Office 365 w usłudze Microsoft Defender
ms.openlocfilehash: 086ea200b6f8519c487622d02ba2d2fc8347f68a
ms.sourcegitcommit: bc35c7826e3403f259725ac72cca5bafd36aa56a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2022
ms.locfileid: "66554208"
---
# <a name="about-the-microsoft-defender-for-office-365-trial"></a>Informacje o wersji próbnej Ochrona usługi Office 365 w usłudze Microsoft Defender

> [!IMPORTANT]
> Szybko rozpocznij pracę z naszym łatwym w użyciu [podręcznikiem wersji próbnej dla Ochrona usługi Office 365 w usłudze Microsoft Defender](trial-playbook-defender-for-office-365.md). Ten podręcznik pomoże Ci w maksymalnym użyciu bezpłatnej wersji próbnej, pokazując, jak chronić organizację za pomocą Ochrona usługi Office 365 w usłudze Microsoft Defender.

Ochrona usługi Office 365 w usłudze Microsoft Defender chroni organizację przed złośliwymi zagrożeniami, które są stwarzane przez wiadomości e-mail, linki (adresy URL) i narzędzia do współpracy. Ochrona usługi Office 365 w usłudze Defender obejmuje:

- **Zasady ochrony przed zagrożeniami**: zdefiniuj zasady ochrony przed zagrożeniami, aby ustawić odpowiedni poziom ochrony organizacji.
- **Raporty**: wyświetlanie raportów w czasie rzeczywistym w celu monitorowania wydajności Ochrona usługi Office 365 w usłudze Defender w organizacji.
- **Możliwości badania zagrożeń i reagowania na** nie: użyj wiodących narzędzi do badania, zrozumienia, symulowania i zapobiegania zagrożeniom.
- **Funkcje zautomatyzowanego badania i reagowania**: oszczędzaj czas i nakład pracy na badanie i ograniczanie zagrożeń.

Wersja próbna Ochrona usługi Office 365 w usłudze Microsoft Defender to prosty sposób na wypróbowanie możliwości Ochrona usługi Office 365 w usłudze Defender planu 2 za darmo, po kilku kliknięciach. Te funkcje wysokiego poziomu zostały opisane w poniższej tabeli:

|Funkcja|Opis|
|---|---|
|[Ustawienia wyłączności w zasadach ochrony przed wyłudzaniem informacji](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)|Uzyskaj ochronę przed personifikacją użytkowników, ochronę przed personifikacją domeny, analizę skrzynki pocztowej i zaawansowane progi wyłudzania informacji.|
|[Bezpieczne załączniki](safe-attachments.md)|Sprawdź załączniki wiadomości e-mail i inne pliki w kontrolowanym środowisku detonacji, aby wykryć nowe i wymijające złośliwe oprogramowanie.|
|[Bezpieczne linki](safe-links.md)|Wykonaj sprawdzanie czasu kliknięcia, aby upewnić się, że adresy URL, które mogły przejść wstępną inspekcję, nie zostały uzbrojone.|
|[Monitory zagrożeń](threat-trackers.md)<sup>\*</sup>|Użyj widżetów i widoków informacyjnych, aby zidentyfikować problemy z cyberbezpieczeństwem, które mogą mieć wpływ na organizację.|
|[Eksplorator zagrożeń](threat-explorer.md)<sup>\*</sup>|W Office 365 wiadomości e-mail można wyszukiwać informacje o zagrożeniach niemal w czasie rzeczywistym.|
|[Zautomatyzowane badanie i reagowanie (AIR)](office-365-air.md)<sup>\*</sup>|Automatycznie lokalizuj i koryguj obiekty zagrożeń w miarę wyzwalania alertów.|
|[Trenowanie symulacji ataków](attack-simulation-training.md)<sup>\*</sup>|Wytrenuj użytkowników, aby identyfikowali ataki wyłudzające informacje i odpowiednio reagowali.|
|[Widoki kampanii](campaigns.md)<sup>\*</sup>|Badanie złośliwych działań poczty e-mail i reagowanie na nie na dużą skalę.|
|[Raporty korzystające z funkcji Ochrona usługi Office 365 w usłudze Defender](view-reports-for-mdo.md)|Wyświetl raporty, w tym stan ochrony przed zagrożeniami, ochronę przed zagrożeniami adresu URL, opóźnienie poczty i inne.|
|[Priorytetowa ochrona konta](/microsoft-365/admin/setup/priority-accounts)<sup>\*</sup>|Użytkownicy identyfikowani jako konta priorytetowe są oznaczani w alertach, raportach i badaniach, aby się wyróżniali. Możesz również użyć tagu Priorytet w filtrach.|

<sup>\*</sup>Ta funkcja jest dostępna wyłącznie w Ochrona usługi Office 365 w usłudze Defender planie 2.

## <a name="set-up-a-defender-for-office-365-trial"></a>Konfigurowanie wersji próbnej Ochrona usługi Office 365 w usłudze Defender

Wersja próbna umożliwia organizacjom łatwe konfigurowanie i konfigurowanie Ochrona usługi Office 365 w usłudze Defender możliwości. Podczas konfigurowania zasady, które są wyłączne dla Ochrona usługi Office 365 w usłudze Defender (w szczególności [bezpieczne załączniki dla wiadomości e-mail](safe-attachments.md), [bezpieczne linki do wiadomości e-mail i usługi Microsoft Teams](safe-links.md) oraz [ochrona przed personifikacją w zasadach ochrony przed wyłudzaniem informacji](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)) są stosowane przy użyciu szablonu Standardowa dla [wstępnie ustawionych zasad zabezpieczeń](preset-security-policies.md).

Domyślnie te zasady są ograniczone do wszystkich użytkowników w organizacji, ale podczas konfiguracji wersji próbnej lub po jej zakończeniu można zmienić przypisanie zasad na określonych użytkowników.

> [!NOTE]
> Istniejące zasady ochrony przed spamem są prawdopodobnie skonfigurowane za pomocą akcji **Przenieś wiadomość do folderu Wiadomości-śmieci, aby** uzyskać werdykt dotyczący spamu o wysokim poziomie ufności w zasadach ochrony przed spamem. Szablon Standardowy dla wstępnie ustawionych zasad zabezpieczeń używa akcji **Komunikat kwarantanny** w celu zapewnienia dużego ufności spamu, a wstępnie ustawione zasady zabezpieczeń są zawsze stosowane przed niestandardowymi zasadami ochrony przed spamem lub domyślnymi zasadami ochrony przed spamem. Aby uzyskać więcej informacji na temat ustawień domyślnych, standardowych i ścisłych, zobacz [Zalecane ustawienia dotyczące operacji EOP i zabezpieczeń Ochrona usługi Office 365 w usłudze Microsoft Defender](recommended-settings-for-eop-and-office365.md).

Inne obciążenia są również dostępne do ochrony (na przykład [bezpieczne załączniki dla programów SharePoint, OneDrive i Microsoft Teams](mdo-for-spo-odb-and-teams.md) oraz [bezpieczne linki do obsługiwanych aplikacji Office 365](safe-links.md#safe-links-settings-for-office-365-apps).

Podczas konfigurowania wersji próbnej funkcje reagowania, które są dostępne wyłącznie dla planu Ochrona usługi Office 365 w usłudze Defender 2 (na przykład [air](office-365-air.md) i [Eksplorator zagrożeń](threat-explorer.md) są również skonfigurowane dla całej organizacji. Nie jest wymagane określanie zakresu zasad.

## <a name="licensing"></a>Licencjonowanie

W ramach konfiguracji wersji próbnej licencje Ochrona usługi Office 365 w usłudze Defender są automatycznie stosowane do organizacji. Licencje są bezpłatne przez pierwsze 90 dni.

Karta licencjonowania dla wersji próbnej zawiera następujące informacje:

:::image type="content" source="../../media/mdo-trial-licensing-card.png" alt-text="Karta Licencjonowanie w wersji próbnej Ochrona usługi Office 365 w usłudze Microsoft Defender" lightbox="../../media/mdo-trial-licensing-card.png":::

- Sekcja **Typ użycia**:
  - **Wersja próbna**: liczba licencji Ochrona usługi Office 365 w usłudze Defender wersji próbnej, które są dostępne do użycia.

    > [!NOTE]
    > W innych lokalizacjach może zostać wyświetlona wartość 300 dla liczby dostępnych licencji wersji próbnej. Ta wartość jest nieprawidłowa (chyba że organizacja ma dokładnie 300 użytkowników). Liczba dostępnych licencji próbnych odpowiada rozmiarowi organizacji, a nie dowolnej wartości 300.

  - **Płatne**: liczba płatnych licencji Ochrona usługi Office 365 w usłudze Defender (jeśli istnieje).

- Sekcja **użycia**: ilu użytkowników jest objętych zasadami Ochrona usługi Office 365 w usłudze Defender.
  - **Wykrywanie tylko & odpowiedzi**: całkowita liczba użytkowników uwzględnionych w następujących scenariuszach:
    - W trakcie okresu próbnego zasady zostały ograniczone do określonych użytkowników.
    - Masz niestandardowe zasady, które są ograniczone do określonych użytkowników.
  - **Pełna ochrona**: całkowita liczba użytkowników chronionych przez funkcje planu Ochrona usługi Office 365 w usłudze Defender 2 (AIR, Threat Explorer, szkolenie symulacji ataków itp.).

Aby uzyskać informacje o cenach, zobacz [Ochrona usługi Office 365 w usłudze Microsoft Defender](https://www.microsoft.com/security/business/siem-and-xdr/microsoft-defender-office-365).

## <a name="permissions"></a>Uprawnienia

Aby rozpocząć lub zakończyć próbę, musisz być członkiem ról **administratora globalnego** lub **administratora zabezpieczeń** w usłudze Azure Active Directory. Aby uzyskać szczegółowe informacje, zobacz [Informacje o rolach administratora](../../admin/add-users/about-admin-roles.md).

## <a name="additional-information"></a>Informacje dodatkowe

Po rozpoczęciu wersji próbnej może upłynąć do 2 godzin, aż zmiany i aktualizacje będą dostępne. Administratorzy muszą wylogować się i zalogować się ponownie, aby zobaczyć zmiany.

## <a name="availability"></a>Dostępność

Wersja próbna Ochrona usługi Office 365 w usłudze Defender jest stopniowo wdrażana dla istniejących klientów, którzy spełniają określone kryteria i którzy nie mają istniejących licencji Ochrona usługi Office 365 w usłudze Defender plan 2 (uwzględnionych w subskrypcji lub jako dodatek).

## <a name="terms-and-conditions"></a>Warunki i postanowienia

Aby uzyskać więcej informacji, zobacz [Ochrona usługi Office 365 w usłudze Microsoft Defender Warunki & wersji próbnej](defender-for-office-365-trial-terms-and-conditions.md).

## <a name="frequently-asked-questions"></a>Często zadawane pytania

### <a name="q-how-do-i-extend-the-trial"></a>Pyt.: Jak mogę przedłużyć wersję próbną?

Ods.: Zobacz [Rozszerzanie wersji próbnej](/microsoft-365/commerce/try-or-buy-microsoft-365#extend-your-trial).

### <a name="q-what-happens-to-my-data-after-the-trial-expires"></a>Pyt.: Co się stanie z moimi danymi po wygaśnięciu wersji próbnej?

Odp.: Po wygaśnięciu wersji próbnej będziesz mieć dostęp do danych wersji próbnej (danych z funkcji w Ochrona usługi Office 365 w usłudze Defender, które nie były wcześniej dostępne) przez 30 dni. Po upływie tego 30 dni wszystkie zasady i dane skojarzone z Ochrona usługi Office 365 w usłudze Defender wersji próbnej zostaną usunięte.

### <a name="q-how-many-times-can-i-use-the-defender-for-office-365-trial-in-my-organization"></a>Pyt.: Ile razy mogę użyć wersji próbnej Ochrona usługi Office 365 w usłudze Defender w mojej organizacji?

Odjęcie: maksymalnie 2 razy. Jeśli pierwsza wersja próbna wygaśnie, musisz poczekać co najmniej 30 dni od daty wygaśnięcia, zanim będzie można ponownie zarejestrować się w Ochrona usługi Office 365 w usłudze Defender wersji próbnej. Po drugiej wersji próbnej nie można zarejestrować się w innej wersji próbnej.

## <a name="learn-more-about-defender-for-office-365"></a>Dowiedz się więcej o Ochrona usługi Office 365 w usłudze Defender

Ochrona usługi Office 365 w usłudze Defender pomaga organizacjom zabezpieczyć swoje przedsiębiorstwo, oferując kompleksową gamę możliwości.

Więcej informacji na temat Ochrona usługi Office 365 w usłudze Defender można również znaleźć w tym [interaktywnym przewodniku](https://aka.ms/MS365D.InteractiveGuide).

:::image type="content" source="../../media/microsoft-defender-for-office-365.png" alt-text="Diagram koncepcyjny Ochrona usługi Office 365 w usłudze Microsoft Defender" lightbox="../../media/microsoft-defender-for-office-365.png":::

### <a name="prevention"></a>Zapobiegania

Niezawodny stos filtrowania zapobiega szerokiej gamie ataków opartych na woluminach i ukierunkowanych, takich jak naruszenia zabezpieczeń poczty e-mail w firmie, wyłudzanie poświadczeń, oprogramowanie wymuszające okup i zaawansowane złośliwe oprogramowanie.

- [Zasady ochrony przed wyłudzaniem informacji: ustawienia wyłączności w Ochrona usługi Office 365 w usłudze Defender](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
- [Bezpieczne załączniki](safe-attachments.md)
- [Bezpieczne linki](safe-links.md)

### <a name="detection"></a>Wykrywania

Wiodąca w branży sztuczna inteligencja wykrywa złośliwą i podejrzaną zawartość oraz koreluje wzorce ataków w celu zidentyfikowania kampanii mających na celu uniknięcie ochrony.

- [Widoki kampanii w ochronie usługi Office 365 w usłudze Microsoft Defender](campaigns.md)

### <a name="investigation-and-hunting"></a>Badanie i wyszukiwanie zagrożeń

Zaawansowane środowiska ułatwiają identyfikowanie, określanie priorytetów i badanie zagrożeń przy użyciu zaawansowanych możliwości wyszukiwania zagrożeń w celu śledzenia ataków w Office 365.

- [Wykrywanie zagrożeń i Eksploratora zagrożeń w czasie rzeczywistym](threat-explorer.md)
- [Raporty w czasie rzeczywistym w Ochrona usługi Office 365 w usłudze Defender](view-reports-for-mdo.md)
- [Monitory zagrożeń — nowe i godne uwagi](threat-trackers.md)
- Integracja z [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

### <a name="response-and-remediation"></a>Odpowiedź i korygowanie

Rozbudowane możliwości reagowania na zdarzenia i automatyzacji wzmacniają skuteczność i wydajność zespołu ds. zabezpieczeń.

- [Zautomatyzowane badanie i reagowanie (AIR) w Ochrona usługi Office 365 w usłudze Microsoft Defender](office-365-air.md)

### <a name="awareness-and-training"></a>Świadomość i szkolenie

Rozbudowane możliwości symulacji i trenowania oraz zintegrowane środowiska w aplikacjach klienckich tworzą świadomość użytkowników.

- [Wprowadzenie do szkolenia z symulacji ataku](attack-simulation-training-get-started.md)

### <a name="security-posture"></a>Stan zabezpieczeń

Zalecane szablony i szczegółowe informacje o konfiguracji pomagają klientom uzyskać i zachować bezpieczeństwo.

- [Wstępne ustawienie zasad zabezpieczeń w usłudze EOP i ochronie usługi Office 365 w usłudze Microsoft Defender](preset-security-policies.md)
- [Analizator konfiguracji dla zasad ochrony w ramach operacji EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender](configuration-analyzer-for-security-policies.md).

## <a name="give-feedback"></a>Przekaż opinię

Twoja opinia pomaga nam lepiej chronić środowisko przed zaawansowanymi atakami. Podziel się swoim doświadczeniem i wrażeniami z możliwości produktów i wyników próbnych.
