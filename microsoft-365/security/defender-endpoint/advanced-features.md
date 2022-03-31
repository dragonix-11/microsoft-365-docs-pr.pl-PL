---
title: Konfigurowanie funkcji zaawansowanych w aplikacji Ochrona punktu końcowego w usłudze Microsoft Defender
description: Włącz funkcje zaawansowane, takie jak blokowanie pliku w Ochrona punktu końcowego w usłudze Microsoft Defender.
keywords: funkcje zaawansowane, ustawienia, plik zablokowany, zautomatyzowane badanie, automatyczne rozwiązywanie, skype, microsoft defender for identity, office 365, azure information protection, intune
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 94e5b18ab1090f6fb76cb7734e90411b93b444e7
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465460"
---
# <a name="configure-advanced-features-in-defender-for-endpoint"></a>Konfigurowanie funkcji zaawansowanych w programie Defender for Endpoint

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-advancedfeats-abovefoldlink)

W zależności od produktów zabezpieczeń firmy Microsoft, z których korzystasz, mogą być dostępne niektóre zaawansowane funkcje integracji usługi Defender for Endpoint z.

## <a name="enable-advanced-features"></a>Włączanie funkcji zaawansowanych

1. W okienku nawigacji **wybierz pozycję Ustawienia** \> **zaawansowane punkty** \> **końcowe**.
2. Wybierz funkcję zaawansowaną, którą chcesz skonfigurować, i przełącz ustawienie **między włączoną** i **wyłączoną**.
3. Kliknij **pozycję Zapisz preferencje**.

Poniższe funkcje zaawansowane są dostępne w celu uzyskania lepszej ochrony przed potencjalnie złośliwymi plikami i uzyskania lepszego wglądu podczas analizy zabezpieczeń.

## <a name="automated-investigation"></a>Zautomatyzowane badanie

Włącz tę funkcję, aby korzystać z funkcji automatycznego badania i rozwiązywania problemów w usłudze. Aby uzyskać więcej informacji, zobacz [Automatyczne badanie](automated-investigations.md).

## <a name="live-response"></a>Odpowiedź na żywo

> [!NOTE]
> Odpowiedź na **żywo wymaga włączenia** automatycznego badania przed włączeniem jej w sekcji ustawień zaawansowanych w portalu Ochrona punktu końcowego w usłudze Microsoft Defender zaawansowanej.

Włącz tę funkcję, aby użytkownicy z odpowiednimi uprawnieniami mogą rozpocząć sesję odpowiedzi na żywo na urządzeniach.

Aby uzyskać więcej informacji na temat przypisań ról, zobacz [Tworzenie ról i zarządzanie nimi](user-roles.md).

## <a name="live-response-for-servers"></a>Odpowiedź na żywo dla serwerów

Włącz tę funkcję, aby użytkownicy z odpowiednimi uprawnieniami mogą rozpocząć sesję odpowiedzi na żywo na serwerach.

Aby uzyskać więcej informacji na temat przypisań ról, zobacz [Tworzenie ról i zarządzanie nimi](user-roles.md).

## <a name="live-response-unsigned-script-execution"></a>Niepodpisane wykonywanie skryptu przez odpowiedź na żywo

Włączenie tej funkcji umożliwia uruchamianie niepodpisanych skryptów w sesji odpowiedzi na żywo.

## <a name="always-remediate-pua"></a>Zawsze reakusywuj środki pua

Potencjalnie niechciane aplikacje (PUA) to kategoria oprogramowania, która może powodować powolne uruchamianie komputera, wyświetlanie nieoczekiwanych reklam lub w najgorszej sytuacji, instalowanie innego oprogramowania, które może być nieoczekiwane lub niechciane.

Włącz tę funkcję, aby potencjalne niechciane aplikacje były naprawiane na wszystkich urządzeniach w dzierżawie, nawet jeśli na tych urządzeniach nie skonfigurowano ochrony za pomocą funkcji PUA. Ta aktywacja tej funkcji pomaga chronić użytkowników przed nieumyślnym zainstalowaniem niechcianych aplikacji na ich urządzeniach. Gdy jest wyłączona, działania naprawcze zależą od konfiguracji urządzenia.

## <a name="restrict-correlation-to-within-scoped-device-groups"></a>Ograniczanie korelacji do grup urządzeń z zakresem

Tej konfiguracji można używać w scenariuszach, w których lokalne operacje SOC powinny ograniczać korelacje alertów tylko do grup urządzeń, do których mogą uzyskać dostęp. Włączenie tego ustawienia spowoduje, że zdarzenie składające się z alertów dotyczących różnych grup urządzeń nie będzie już traktowane jako jedno zdarzenie. Lokalny soC może podjąć działania w związku z tym incydentem, ponieważ ma dostęp do jednej z grup urządzeń, w których uczestniczy. Jednak globalna soC będzie widzieć kilka różnych zdarzeń według grupy urządzeń zamiast jednego zdarzenia. Nie zalecamy włączania tego ustawienia, chyba że w ten sposób wywrócą korzyści wynikające z korelacji związanej z incydentami w całej organizacji.

> [!NOTE]
> Zmiana tego ustawienia ma wpływ tylko na korelacje alertów w przyszłości.

## <a name="enable-edr-in-block-mode"></a>Włączanie EDR w trybie blokowania

Wykrywanie punktu końcowego i odpowiedź (EDR) w trybie blokowania zapewnia ochronę przed złośliwymi artefaktami nawet wtedy, Program antywirusowy Microsoft Defender działa w trybie pasywnym. Gdy ta tryb jest włączona, EDR trybie blokowania blokuje złośliwe artefakty lub zachowania wykrywane na urządzeniu. EDR trybie blokowania działa w tle w celu korygowania złośliwych artefaktów wykrytych po naruszeniu zabezpieczeń.

## <a name="autoresolve-remediated-alerts"></a>Automatyczne rozwiązywanie problemów z alertami

W przypadku dzierżaw utworzonych w dniu Windows 10, wersja 1809 lub później funkcja automatycznego badania i rozwiązywania problemów jest konfigurowana domyślnie w celu usuwania alertów, w których stan wyników zautomatyzowanej analizy to "Nie znaleziono zagrożeń" lub "Usunięto". Jeśli nie chcesz, aby alerty były rozwiązywane automatycznie, musisz ręcznie wyłączyć tę funkcję.

> [!TIP]
> W przypadku dzierżaw utworzonych przed tą wersją należy ręcznie włączyć tę funkcję ze [strony Funkcje zaawansowane](https://security.microsoft.com//preferences2/integration) .

> [!NOTE]
>
> - Wynik akcji automatycznego rozwiązywania problemów może mieć wpływ na obliczanie poziomu ryzyka urządzenia oparte na aktywnych alertach na urządzeniu.
> - Jeśli analityk operacji zabezpieczeń ręcznie ustawia stan alertu na "W toku" lub "Rozwiązano", funkcja automatycznego rozpoznawania nie zastąpi jej.

## <a name="allow-or-block-file"></a>Zezwalanie na plik lub blokowanie go

Blokowanie jest dostępne tylko wtedy, gdy Twoja organizacja spełnia następujące wymagania:

- Używa Program antywirusowy Microsoft Defender jako aktywnego rozwiązania zapobiegającego złośliwym oprogramowaniem, oraz
- Funkcja ochrony opartej na chmurze jest włączona

Ta funkcja umożliwia blokowanie potencjalnie złośliwych plików w sieci. Zablokowanie pliku uniemożliwi jego odczytanie, napisane lub wykonanie na urządzeniach w Twojej organizacji.

Aby **włączyć opcję Zezwalaj na pliki lub blokuj** je:

1. W okienku nawigacji **wybierz pozycję Ustawienia** \> **punkty końcowe** \> **Ogólne** \> **funkcje zaawansowane Zezwalaj** \> **na plik lub blokuj go**.

1. Przełącz ustawienie w opcji **Wł. i** **Wył**.
 
    :::image type="content" source="../../media/alloworblockfile.png" alt-text="Ekran Punkty końcowe" lightbox="../../media/alloworblockfile.png":::

1. Wybierz **pozycję Zapisz** preferencje u dołu strony.

Po włączeniu tej funkcji możesz blokować pliki [](respond-file-alerts.md#allow-or-block-file) za pomocą karty **Dodaj** wskaźnik na stronie profilu pliku.

## <a name="custom-network-indicators"></a>Niestandardowe wskaźniki sieci

Włączenie tej funkcji umożliwia tworzenie wskaźników dla adresów IP, domen lub adresów URL, które określają, czy będą one dozwolone, czy blokowane na podstawie niestandardowej listy wskaźników.

Aby korzystać z tej funkcji, urządzenia muszą być uruchomione Windows 10 wersji 1709 lub nowszej albo Windows 11. Powinny one również mieć ochronę sieci w trybie blokowania i w wersji 4.18.1906.3 lub nowszej platformy ochrony przed złośliwym [oprogramowaniem, zobacz artykuł KB 4052623](https://go.microsoft.com/fwlink/?linkid=2099834).

Aby uzyskać więcej informacji, zobacz [Zarządzanie wskaźnikami](manage-indicators.md).

> [!NOTE]
> Ochrona sieci korzysta z usług reputacji, które przetwarzają żądania w lokalizacjach, które mogą być spoza lokalizacji wybranej dla danych programu Defender dla punktów końcowych.

## <a name="tamper-protection"></a>Ochrona przed naruszeniami
W przypadku niektórych rodzajów cyberataków złe szybki próbują wyłączyć na komputerach funkcje zabezpieczeń, takie jak ochrona przed wirusami. Bad  na przykład w celu wyłączenia funkcji zabezpieczeń, aby uzyskać łatwiejszy dostęp do danych, zainstalować złośliwe oprogramowanie lub w inny sposób wykorzystać dane, tożsamość i urządzenia.

Ochrona przed naruszeniami w zasadzie blokuje Program antywirusowy Microsoft Defender i zapobiega zmienianiu ustawień zabezpieczeń za pomocą aplikacji i metod.

Ta funkcja jest dostępna, jeśli Twoja organizacja Program antywirusowy Microsoft Defender i jest włączona ochrona oparta na chmurze. Aby uzyskać więcej informacji, zobacz [Używanie technologii następnej generacji w programach Program antywirusowy Microsoft Defender za pośrednictwem ochrony chmury](cloud-protection-microsoft-defender-antivirus.md).

Zachowaj włączona ochronę przed naruszeniami, aby zapobiec niepożądanym zmianom rozwiązania zabezpieczeń i jego podstawowych funkcji.

## <a name="show-user-details"></a>Pokaż szczegóły użytkownika

Włącz tę funkcję, aby wyświetlić szczegóły użytkowników przechowywane w Azure Active Directory. Szczegóły obejmują obraz, nazwę, tytuł i informacje działu użytkownika podczas badania jednostek konta użytkownika. Informacje o koncie użytkownika można znaleźć w następujących widokach:

- Pulpit nawigacyjny operacji zabezpieczeń
- Kolejka alertów
- Strona szczegółów urządzenia

Aby uzyskać więcej informacji, zobacz [Badanie konta użytkownika](investigate-user.md).

## <a name="skype-for-business-integration"></a>Skype dla firm integracji z usługą

Włączenie integracji Skype dla firm klienta umożliwia komunikowanie się z użytkownikami za pomocą Skype dla firm, poczty e-mail lub telefonu. Ta aktywacja może być przydatna, gdy musisz się komunikować z użytkownikiem i zminimalizować ryzyko.

> [!NOTE]
> Gdy urządzenie jest odizolowane od sieci, pojawia się okno podręczne, w którym możesz włączyć komunikację między firmami Outlook i Skype, która umożliwia komunikację z użytkownikiem w przypadku rozłączenia z siecią. To ustawienie dotyczy trybu Skype i Outlook, gdy urządzenia są w trybie izolacji.

## <a name="microsoft-defender-for-identity-integration"></a>Microsoft Defender for Identity integracji z usługą

Integracja z usługą Microsoft Defender for Identity umożliwia bezpośrednie prze przestawnienie do innego produktu zabezpieczeń tożsamości firmy Microsoft. Microsoft Defender for Identity rozszerzy analizę o więcej informacji o podejrzanym, naruszonym koncie i powiązanych zasobach. Włączenie tej funkcji wzbogaci możliwości badania oparte na urządzeniach przez przestawiania ich w sieci z punktu widzenia identyfikacji.

> [!NOTE]
> Aby włączyć tę funkcję, musisz mieć odpowiednią licencję.

## <a name="office-365-threat-intelligence-connection"></a>Office 365 połączenia analizy zagrożeń

Ta funkcja jest dostępna tylko w przypadku aktywnego Office 365 E5 lub dodatku Threat Intelligence. Aby uzyskać więcej informacji, zobacz stronę produktu Office 365 Enterprise E5.

Po włączeniu tej funkcji będzie można dołączać dane z usługi Ochrona usługi Office 365 w usłudze Microsoft Defender do usługi Microsoft 365 Defender w celu przeprowadzenia kompleksowego badania zabezpieczeń w skrzynkach pocztowych i Office 365 i Windows .

> [!NOTE]
> Aby włączyć tę funkcję, musisz mieć odpowiednią licencję.

Aby otrzymywać kontekstową integrację urządzeń z usługą Office 365 analizą zagrożeń, musisz włączyć ustawienia usługi Defender for Endpoint na pulpicie nawigacyjnym Zabezpieczenia & zgodności. Aby uzyskać więcej informacji, zobacz [Badanie zagrożeń i odpowiedź na nie](/microsoft-365/security/office-365-security/office-365-ti).

## <a name="microsoft-threat-experts---targeted-attack-notifications"></a>Microsoft Threat Experts — powiadomienia o atakach ukierunkowanych

Spośród dwóch składników Microsoft Threat Expert powiadomienie o atakach kierowane jest ogólnie dostępne. Funkcja ekspertów na żądanie jest nadal w wersji zapoznawczej. Możesz korzystać z funkcji ekspertów na żądanie tylko wtedy, gdy wniosek o podgląd został zatwierdzony. Możesz otrzymywać powiadomienia o ukierunkowanych atakach z usługi Microsoft Threat Experts za pośrednictwem pulpitu nawigacyjnego alertów portalu punktów końcowych usługi Defender oraz za pośrednictwem poczty e-mail, jeśli go konfigurujesz.

> [!NOTE]
> Funkcja Microsoft Threat Experts Defender for Endpoint jest dostępna w licencji E5 [dla Enterprise Mobility + Security.](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)

## <a name="microsoft-defender-for-cloud-apps"></a>Microsoft Defender for Cloud Apps

Włączenie tego ustawienia przekazuje sygnał usługi Defender for Endpoint do Microsoft Defender for Cloud Apps w celu zapewnienia bardziej dogłębnej widoczności użycia aplikacji w chmurze. Dane przekazane są przechowywane i przetwarzane w tej samej lokalizacji, w Defender dla Chmury danych aplikacji.

> [!NOTE]
> Ta funkcja będzie dostępna w licencji E5 dla systemu [Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility-security) na urządzeniach z systemem Windows 10 w wersji 1709 (kompilacja systemu operacyjnego 16299.1085 z [kb4493441](https://support.microsoft.com/help/4493441)), Windows 10 wersja 1803 (kompilacja systemu operacyjnego 17134.704 z [kb4493464](https://support.microsoft.com/help/4493464)), Windows 10, wersja 1809  (Kompilacja 17763.379 systemu operacyjnego z [kb4489899](https://support.microsoft.com/help/4489899)), nowsze wersje Windows 10 lub Windows 11.

### <a name="enable-the-microsoft-defender-for-endpoint-integration-from-the-microsoft-defender-for-identity-portal"></a>Włączanie integracji Ochrona punktu końcowego w usłudze Microsoft Defender klienta z Microsoft Defender for Identity sieci Microsoft Defender for Identity

Aby uzyskać kontekstowe integracja urządzeń w aplikacji Microsoft Defender for Identity, musisz również włączyć tę funkcję w portalu Microsoft Defender for Identity sieci.

1. Zaloguj się do portalu [Microsoft Defender for Identity przy](https://portal.atp.azure.com/) użyciu roli administratora globalnego lub administratora zabezpieczeń.

2. Kliknij **pozycję Utwórz wystąpienie**.

3. Przełącz ustawienie Integracja **na Włącz i** kliknij przycisk **Zapisz**.

Po zakończeniu kroków integracji w obu portalach odpowiednie alerty będą się mogły wyświetlić na stronie szczegółów urządzenia lub szczegółów użytkownika.

## <a name="web-content-filtering"></a>Filtrowanie zawartości sieci Web

Blokowanie dostępu do witryn internetowych zawierających niechcianą zawartość i śledzenie aktywności w sieci Web we wszystkich domenach. Aby określić kategorie zawartości sieci Web, które chcesz blokować, utwórz zasady filtrowania [zawartości sieci Web](https://security.microsoft.com/preferences2/web_content_filtering_policy). Upewnij się, że podczas wdrażania planu bazowego zabezpieczeń sieci w trybie [blokowania Ochrona punktu końcowego w usłudze Microsoft Defender zabezpieczeń](https://devicemanagement.microsoft.com/#blade/Microsoft_Intune_Workflows/SecurityBaselineSummaryMenu/overview/templateType/2).

## <a name="share-endpoint-alerts-with-microsoft-compliance-center"></a>Udostępnianie alertów punktu końcowego za pomocą Centrum zgodności firmy Microsoft

Przesyła dalej alerty zabezpieczeń punktów końcowych i ich stan kontroli do Centrum zgodności firmy Microsoft, co pozwala na ulepszanie zasad zarządzania ryzykiem w niejawnym programie testów za pomocą alertów i korygowanie wewnętrznych zagrożeń, zanim spowodują krzywdę. Dane przekazane są przetwarzane i przechowywane w tej samej lokalizacji, w Office 365 danych.

Po skonfigurowaniu [wskaźników](/microsoft-365/compliance/insider-risk-management-settings#indicators) naruszenia zasad zabezpieczeń w ustawieniach zarządzania ryzykiem w niejawnym programie testów alerty usługi Defender for Endpoint będą udostępniane właściwej użytkownikom zarządzania ryzykiem w niejawnym programie testów.

## <a name="microsoft-intune-connection"></a>Microsoft Intune połączeń

Program Defender for Endpoint można zintegrować z [programem Microsoft Intune](/intune/what-is-intune) w celu umożliwienia [dostępu warunkowego opartego na ryzyku urządzenia](/intune/advanced-threat-protection#enable-windows-defender-atp-in-intune). Po włączeniu [tej funkcji](configure-conditional-access.md) będzie można udostępnić programowi Defender for Endpoint informacje o urządzeniu z programem Intune, poprawiając wymuszanie zasad.

> [!IMPORTANT]
> Aby korzystać z tej funkcji, należy włączyć integrację zarówno z usługą Intune, jak i usługą Defender for Endpoint. Aby uzyskać więcej informacji na temat poszczególnych kroków, zobacz [Konfigurowanie dostępu warunkowego w programie Defender dla punktu końcowego](configure-conditional-access.md).

Ta funkcja jest dostępna tylko w przypadku następujących wymagań wstępnych:

- Dzierżawa licencjonowana dla usług Enterprise Mobility + Security E3 i Windows E5 (lub Microsoft 365 Enterprise E5)
- Aktywne środowisko Microsoft Intune z dołączanym Intune i Windows [Azure AD](/azure/active-directory/devices/concept-azure-ad-join/).

### <a name="conditional-access-policy"></a>Zasady dostępu warunkowego

Włączenie integracji Intune warunkowej Intune automatyczne utworzenie klasycznych zasad dostępu warunkowego(UC). Te klasyczne zasady certyfikacji są wymagane do konfigurowania raportów o stanie w celu Intune. Nie należy go usuwać.

> [!NOTE]
> Klasyczne zasady certyfikacji utworzone przez Intune różnią się od nowoczesnych zasad dostępu warunkowego[, które](/azure/active-directory/conditional-access/overview/) są używane do konfigurowania punktów końcowych.

## <a name="device-discovery"></a>Odnajdowanie urządzeń

Ułatwia znajdowanie nieza zarządzania urządzeniami połączonymi z siecią firmową bez konieczności dodatkowych urządzeń czy uciążliwych zmian w procesach. Korzystając z urządzeń podłączonych do urządzenia, możesz znaleźć urządzenia niezakierowane w twojej sieci oraz oceniać luki w zabezpieczeniach i zagrożenia. Aby uzyskać więcej informacji, zobacz [Odnajdowanie urządzeń](device-discovery.md).

> [!NOTE]
> Zawsze możesz zastosować filtry, aby wykluczyć urządzenia nieza zarządzanie z listy zasobów w spisie urządzeń. Możesz również użyć kolumny stanu dołączania w zapytaniach interfejsu API, aby odfiltrować urządzenia nieza zarządzanie.

## <a name="preview-features"></a>Funkcje wersji Preview

Dowiedz się więcej o nowych funkcjach w programie Defender for Endpoint Preview. Wypróbuj nadchodzące funkcje, włączając środowisko wersji Preview.

Będziesz mieć dostęp do nadchodzących funkcji, na temat których możesz przekazać opinię, aby ulepszyć ogólne środowisko, zanim funkcje będą ogólnie dostępne.

## <a name="download-quarantined-files"></a>Pobieranie plików poddanych kwarantannie

Poddaj kopię zapasową kwarantannie plików w bezpiecznym i zgodnym miejscu, aby można je było pobrać bezpośrednio z kwarantanny. Przycisk **Pobierz** plik będzie zawsze dostępny na stronie pliku. To ustawienie jest domyślnie włączone. [Dowiedz się więcej o wymaganiach](respond-file-alerts.md#download-quarantined-files)

## <a name="related-topics"></a>Tematy pokrewne

- [Aktualizowanie ustawień przechowywania danych](data-retention-settings.md)
- [Konfigurowanie powiadomień alertów](configure-email-notifications.md)
