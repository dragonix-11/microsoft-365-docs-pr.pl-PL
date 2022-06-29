---
title: Konfigurowanie zaawansowanych funkcji w Ochrona punktu końcowego w usłudze Microsoft Defender
description: Włącz zaawansowane funkcje, takie jak plik bloków w Ochrona punktu końcowego w usłudze Microsoft Defender.
keywords: zaawansowane funkcje, ustawienia, plik bloku, zautomatyzowane badanie, automatyczne rozpoznawanie, skype, microsoft defender for identity, office 365, azure information protection, intune
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
ms.openlocfilehash: d9824a738468f14ebfc7cd7bdc3c612c21a0e43c
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66493114"
---
# <a name="configure-advanced-features-in-defender-for-endpoint"></a>Konfigurowanie zaawansowanych funkcji w usłudze Defender for Endpoint

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-advancedfeats-abovefoldlink)

W zależności od używanych produktów zabezpieczeń firmy Microsoft niektóre zaawansowane funkcje mogą być dostępne do integracji z usługą Defender for Endpoint.

## <a name="enable-advanced-features"></a>Włączanie zaawansowanych funkcji

1. W okienku nawigacji wybierz pozycję **Ustawienia** \> **Punkty końcowe** \> **Funkcje zaawansowane**.
2. Wybierz zaawansowaną funkcję, którą chcesz skonfigurować, i przełącz ustawienie między **włączaniem** i **wyłączaniem**.
3. Kliknij **pozycję Zapisz preferencje**.

Skorzystaj z następujących zaawansowanych funkcji, aby lepiej chronić się przed potencjalnie złośliwymi plikami i uzyskać lepszy wgląd podczas badań zabezpieczeń.

## <a name="automated-investigation"></a>Zautomatyzowane badanie

Włącz tę funkcję, aby korzystać z funkcji zautomatyzowanego badania i korygowania usługi. Aby uzyskać więcej informacji, zobacz [Zautomatyzowane badanie](automated-investigations.md).

## <a name="live-response"></a>Odpowiedź na żywo

> [!NOTE]
> Odpowiedź na żywo wymaga włączenia **automatycznego badania** przed włączeniem go w sekcji ustawień zaawansowanych w portalu Ochrona punktu końcowego w usłudze Microsoft Defender.

Włącz tę funkcję, aby użytkownicy z odpowiednimi uprawnieniami mogli rozpocząć sesję odpowiedzi na żywo na urządzeniach.

Aby uzyskać więcej informacji na temat przypisań ról, zobacz [Tworzenie ról i zarządzanie nimi](user-roles.md).

## <a name="live-response-for-servers"></a>Odpowiedź na żywo dla serwerów

Włącz tę funkcję, aby użytkownicy z odpowiednimi uprawnieniami mogli rozpocząć sesję odpowiedzi na żywo na serwerach.

Aby uzyskać więcej informacji na temat przypisań ról, zobacz [Tworzenie ról i zarządzanie nimi](user-roles.md).

## <a name="live-response-unsigned-script-execution"></a>Wykonywanie skryptu bez znaku odpowiedzi na żywo

Włączenie tej funkcji umożliwia uruchamianie niepodpisanych skryptów w sesji odpowiedzi na żywo.

## <a name="always-remediate-pua"></a>Zawsze koryguj pua

Potencjalnie niechciane aplikacje (PUA) to kategoria oprogramowania, która może powodować powolne uruchamianie maszyny, wyświetlanie nieoczekiwanych reklam lub w najgorszym przypadku instalowanie innego oprogramowania, które może być nieoczekiwane lub niepożądane.

Włącz tę funkcję, aby potencjalnie niechciane aplikacje (PUA) były korygowane na wszystkich urządzeniach w dzierżawie, nawet jeśli ochrona pua nie jest skonfigurowana na urządzeniach. Ta aktywacja funkcji pomaga chronić użytkowników przed nieumyślnym instalowaniem niechcianych aplikacji na urządzeniu. Po wyłączeniu korygowanie zależy od konfiguracji urządzenia.

## <a name="restrict-correlation-to-within-scoped-device-groups"></a>Ograniczanie korelacji do grupy urządzeń o określonym zakresie

Tej konfiguracji można używać w scenariuszach, w których lokalne operacje SOC chcą ograniczyć korelacje alertów tylko do grup urządzeń, do których mogą uzyskiwać dostęp. Po włączeniu tego ustawienia zdarzenie składające się z alertów, które nie będą już traktowane jako pojedyncze zdarzenie, nie będzie już uznawane za pojedyncze zdarzenie. Lokalna usługa SOC może następnie podjąć działania w związku ze zdarzeniem, ponieważ ma dostęp do jednej z zaangażowanych grup urządzeń. Jednak globalna usługa SOC będzie widzieć kilka różnych zdarzeń według grupy urządzeń zamiast jednego zdarzenia. Nie zalecamy włączania tego ustawienia, chyba że przeważa to nad korzyściami wynikającymi z korelacji zdarzeń w całej organizacji.

> [!NOTE]
> Zmiana tego ustawienia ma wpływ tylko na przyszłe korelacje alertów.

## <a name="enable-edr-in-block-mode"></a>Włączanie EDR w trybie bloku

Wykrywanie i reagowanie na punkty końcowe (EDR) w trybie bloku zapewnia ochronę przed złośliwymi artefaktami, nawet jeśli program antywirusowy Microsoft Defender działa w trybie pasywnym. Po włączeniu program EDR w trybie bloku blokuje złośliwe artefakty lub zachowania wykryte na urządzeniu. EDR w trybie bloku działa w tle, aby korygować złośliwe artefakty, które zostały wykryte po naruszeniu zabezpieczeń.

## <a name="autoresolve-remediated-alerts"></a>Skorygowane alerty autoresolve

W przypadku dzierżaw utworzonych w Windows 10, wersja 1809 lub po nim funkcja automatycznego badania i korygowania jest domyślnie skonfigurowana do rozwiązywania alertów, w których stan wyniku analizy automatycznej to "Nie znaleziono zagrożeń" lub "Skorygowano". Jeśli nie chcesz, aby alerty były automatycznie rozwiązywane, musisz ręcznie wyłączyć tę funkcję.

> [!TIP]
> W przypadku dzierżaw utworzonych przed tą wersją należy ręcznie włączyć tę funkcję na stronie [Funkcje zaawansowane](https://security.microsoft.com//preferences2/integration) .

> [!NOTE]
>
> - Wynik akcji automatycznego rozwiązywania może mieć wpływ na obliczenie poziomu ryzyka urządzenia, które jest oparte na aktywnych alertach znalezionych na urządzeniu.
> - Jeśli analityk operacji zabezpieczeń ręcznie ustawi stan alertu na wartość "W toku" lub "Rozwiązano", funkcja automatycznego rozwiązywania nie zastąpi go.

## <a name="allow-or-block-file"></a>Zezwalaj lub blokuj plik

Blokowanie jest dostępne tylko wtedy, gdy organizacja spełnia następujące wymagania:

- Używa programu antywirusowego Microsoft Defender jako aktywnego rozwiązania chroniącego przed złośliwym kodem i,
- Włączono funkcję ochrony opartą na chmurze

Ta funkcja umożliwia blokowanie potencjalnie złośliwych plików w sieci. Zablokowanie pliku uniemożliwi jego odczyt, zapisanie lub wykonanie na urządzeniach w organizacji.

Aby włączyć **opcję Zezwalaj lub blokuj** pliki:

1. W okienku nawigacji wybierz pozycję **Ustawienia** \> **Punkty końcowe** \> **Ogólne** \> **funkcje** \> zaawansowane **Zezwalaj lub blokuj plik**.

1. Przełącz ustawienie między **włączaniem** i **wyłączaniem**.
 
    :::image type="content" source="../../media/alloworblockfile.png" alt-text="Ekran Punkty końcowe" lightbox="../../media/alloworblockfile.png":::

1. Wybierz pozycję **Zapisz preferencje** w dolnej części strony.

Po włączeniu tej funkcji możesz [zablokować pliki](respond-file-alerts.md#allow-or-block-file) za pośrednictwem karty **Dodaj wskaźnik** na stronie profilu pliku.

## <a name="custom-network-indicators"></a>Niestandardowe wskaźniki sieci

Włączenie tej funkcji umożliwia tworzenie wskaźników dla adresów IP, domen lub adresów URL, które określają, czy będą one dozwolone, czy zablokowane na podstawie niestandardowej listy wskaźników.

Aby korzystać z tej funkcji, urządzenia muszą być uruchomione Windows 10 wersji 1709 lub nowszej lub Windows 11. Powinny one również mieć ochronę sieci w trybie bloku i wersji 4.18.1906.3 lub nowszej platformy ochrony przed złośliwym kodem [, zobacz KB 4052623](https://go.microsoft.com/fwlink/?linkid=2099834).

Aby uzyskać więcej informacji, zobacz [Zarządzanie wskaźnikami](manage-indicators.md).

> [!NOTE]
> Ochrona sieci wykorzystuje usługi reputacji, które przetwarzają żądania w lokalizacjach, które mogą znajdować się poza lokalizacją wybraną dla danych punktu końcowego usługi Defender.

## <a name="tamper-protection"></a>Ochrona przed naruszeniami
Podczas pewnego rodzaju cyberataków źle aktorzy próbują wyłączyć funkcje zabezpieczeń, takie jak ochrona przed wirusami, na maszynach. Źle aktorzy lubią wyłączać funkcje zabezpieczeń, aby uzyskać łatwiejszy dostęp do danych, zainstalować złośliwe oprogramowanie lub w inny sposób wykorzystać dane, tożsamość i urządzenia.

Ochrona przed naruszeniami zasadniczo blokuje program antywirusowy Microsoft Defender i uniemożliwia zmianę ustawień zabezpieczeń za pośrednictwem aplikacji i metod.

Ta funkcja jest dostępna, jeśli twoja organizacja korzysta z programu antywirusowego Microsoft Defender i włączono ochronę opartą na chmurze. Aby uzyskać więcej informacji, zobacz [Korzystanie z technologii nowej generacji w programie antywirusowym Microsoft Defender za pośrednictwem ochrony dostarczanej w chmurze](cloud-protection-microsoft-defender-antivirus.md).

Zachowaj włączoną ochronę przed naruszeniami, aby zapobiec niepożądanym zmianom w rozwiązaniu zabezpieczeń i jego podstawowych funkcjach.

## <a name="show-user-details"></a>Pokaż szczegóły użytkownika

Włącz tę funkcję, aby wyświetlić szczegóły użytkownika przechowywane w usłudze Azure Active Directory. Szczegóły obejmują obraz użytkownika, nazwę, tytuł i informacje o dziale podczas badania jednostek konta użytkownika. Informacje o koncie użytkownika można znaleźć w następujących widokach:

- Pulpit nawigacyjny operacji zabezpieczeń
- Kolejka alertów
- Strona szczegółów urządzenia

Aby uzyskać więcej informacji, zobacz [Badanie konta użytkownika](investigate-user.md).

## <a name="skype-for-business-integration"></a>integracja Skype dla firm

Włączenie integracji Skype dla firm zapewnia możliwość komunikowania się z użytkownikami przy użyciu Skype dla firm, poczty e-mail lub telefonu. Ta aktywacja może być przydatna w przypadku konieczności komunikowania się z użytkownikiem i ograniczania ryzyka.

> [!NOTE]
> Gdy urządzenie jest odizolowane od sieci, istnieje wyskakujące okienko, w którym można włączyć komunikację programu Outlook i Skype, która umożliwia komunikację z użytkownikiem, gdy jest odłączony od sieci. To ustawienie dotyczy komunikacji za pomocą programu Skype i programu Outlook, gdy urządzenia są w trybie izolacji.

## <a name="microsoft-defender-for-identity-integration"></a>integracja Microsoft Defender for Identity

Integracja z usługą Microsoft Defender for Identity umożliwia przejście bezpośrednio do innego produktu zabezpieczeń tożsamości firmy Microsoft. Microsoft Defender for Identity rozszerza badanie o więcej szczegółowych informacji o podejrzanym koncie i powiązanych zasobach. Włączając tę funkcję, wzbogacisz możliwość badania opartego na urządzeniu, przestawiając się w sieci z punktu widzenia identyfikacji.

> [!NOTE]
> Aby włączyć tę funkcję, musisz mieć odpowiednią licencję.

## <a name="office-365-threat-intelligence-connection"></a>połączenie analizy zagrożeń Office 365

Ta funkcja jest dostępna tylko wtedy, gdy masz aktywny Office 365 E5 lub dodatek Analiza zagrożeń. Aby uzyskać więcej informacji, zobacz stronę produktu Office 365 Enterprise E5.

Po włączeniu tej funkcji będzie można włączyć dane z Ochrona usługi Office 365 w usłudze Microsoft Defender do Microsoft 365 Defender, aby przeprowadzić kompleksowe badanie zabezpieczeń na Office 365 skrzynkach pocztowych i urządzeniach z systemem Windows.

> [!NOTE]
> Aby włączyć tę funkcję, musisz mieć odpowiednią licencję.

Aby uzyskać kontekstową integrację urządzeń w usłudze Office 365 Threat Intelligence, musisz włączyć ustawienia usługi Defender for Endpoint na pulpicie nawigacyjnym Security & Compliance. Aby uzyskać więcej informacji, zobacz [Badanie zagrożeń i reagowanie](/microsoft-365/security/office-365-security/office-365-ti).

## <a name="microsoft-threat-experts---targeted-attack-notifications"></a>Microsoft Threat Experts — powiadomienia o atakach ukierunkowanych

Spośród dwóch składników programu Microsoft Threat Expert powiadomienie o ukierunkowanym ataku jest ogólnie dostępne. Funkcja eksperci na żądanie jest nadal dostępna w wersji zapoznawczej. Można korzystać z możliwości ekspertów na żądanie tylko wtedy, gdy złożyłeś wniosek o wersję zapoznawczą i twoja aplikacja została zatwierdzona. Możesz otrzymywać powiadomienia o atakach ukierunkowanych z Microsoft Threat Experts za pośrednictwem pulpitu nawigacyjnego alertów portalu usługi Defender dla punktów końcowych i za pośrednictwem poczty e-mail, jeśli je skonfigurujesz.

> [!NOTE]
> Możliwość Microsoft Threat Experts w usłudze Defender for Endpoint jest dostępna z licencją E5 dla [Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).

## <a name="microsoft-defender-for-cloud-apps"></a>Microsoft Defender for Cloud Apps

Włączenie tego ustawienia przekazuje sygnały usługi Defender for Endpoint do Microsoft Defender for Cloud Apps w celu zapewnienia głębszego wglądu w użycie aplikacji w chmurze. Przekazane dane są przechowywane i przetwarzane w tej samej lokalizacji co dane usługi Defender for Cloud Apps.

> [!NOTE]
> Ta funkcja będzie dostępna z licencją E5 dla [Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility-security) na urządzeniach z systemem Windows 10, wersja 1709 (kompilacja systemu operacyjnego 16299.1085 z [KB4493441](https://support.microsoft.com/help/4493441)), Windows 10, wersja 1803 (kompilacja systemu operacyjnego 17134.704 z [KB4493464](https://support.microsoft.com/help/4493464)), Windows 10, wersja 1809  (Kompilacja systemu operacyjnego 17763.379 z [kb4489899](https://support.microsoft.com/help/4489899)), nowsze wersje Windows 10 lub Windows 11.

### <a name="enable-the-microsoft-defender-for-endpoint-integration-from-the-microsoft-defender-for-identity-portal"></a>Włączanie integracji Ochrona punktu końcowego w usłudze Microsoft Defender z portalu Microsoft Defender for Identity

Aby uzyskać integrację urządzeń kontekstowych w Microsoft Defender for Identity, należy również włączyć tę funkcję w portalu Microsoft Defender for Identity.

1. Zaloguj się do [portalu Microsoft Defender for Identity](https://portal.atp.azure.com/) przy użyciu roli administratora globalnego lub administratora zabezpieczeń.

2. Kliknij **pozycję Utwórz wystąpienie**.

3. Przełącz ustawienie Integracja na **Wł.** , a następnie kliknij przycisk **Zapisz**.

Po wykonaniu kroków integracji w obu portalach będzie można wyświetlić odpowiednie alerty na stronie szczegółów urządzenia lub szczegółów użytkownika.

## <a name="web-content-filtering"></a>Filtrowanie zawartości sieci Web

Blokuj dostęp do witryn internetowych zawierających niepożądaną zawartość i śledź aktywność internetową we wszystkich domenach. Aby określić kategorie zawartości internetowej, które chcesz zablokować, utwórz [zasady filtrowania zawartości internetowej](https://security.microsoft.com/preferences2/web_content_filtering_policy). Upewnij się, że masz ochronę sieci w trybie bloku podczas wdrażania [punktu odniesienia zabezpieczeń Ochrona punktu końcowego w usłudze Microsoft Defender](https://devicemanagement.microsoft.com/#blade/Microsoft_Intune_Workflows/SecurityBaselineSummaryMenu/overview/templateType/2).

## <a name="share-endpoint-alerts-with-microsoft-purview-compliance-portal"></a>Udostępnianie alertów punktu końcowego za pomocą portal zgodności Microsoft Purview

Przekazuje alerty zabezpieczeń punktu końcowego i ich stan klasyfikacji do portal zgodności Microsoft Purview, co pozwala ulepszyć zasady zarządzania ryzykiem wewnętrznym za pomocą alertów i korygować ryzyko wewnętrzne, zanim spowodują one szkody. Przekazane dane są przetwarzane i przechowywane w tej samej lokalizacji co dane Office 365.

Po skonfigurowaniu [wskaźników naruszenia zasad zabezpieczeń](/microsoft-365/compliance/insider-risk-management-settings#indicators) w ustawieniach zarządzania ryzykiem wewnętrznym alerty usługi Defender dla punktów końcowych będą udostępniane odpowiednim użytkownikom za pomocą zarządzania ryzykiem wewnętrznym.

## <a name="authenticated-telemetry"></a>Uwierzytelnione dane telemetryczne

Możesz **włączyć** dane telemetryczne uwierzytelnione, aby zapobiec fałszowaniu danych telemetrycznych na pulpicie nawigacyjnym.

## <a name="microsoft-intune-connection"></a>połączenie Microsoft Intune

Usługę Defender for Endpoint można zintegrować z [Microsoft Intune](/intune/what-is-intune), aby [umożliwić dostęp warunkowy oparty na ryzyku urządzenia](/intune/advanced-threat-protection#enable-windows-defender-atp-in-intune). Po [włączeniu tej funkcji](configure-conditional-access.md) będzie można udostępniać informacje o urządzeniu usługi Defender for Endpoint za pomocą Intune, zwiększając wymuszanie zasad.

> [!IMPORTANT]
> Aby korzystać z tej funkcji, należy włączyć integrację zarówno w Intune, jak i w usłudze Defender for Endpoint. Aby uzyskać więcej informacji na temat konkretnych kroków, zobacz [Konfigurowanie dostępu warunkowego w usłudze Defender for Endpoint](configure-conditional-access.md).

Ta funkcja jest dostępna tylko wtedy, gdy masz następujące wymagania wstępne:

- Licencjonowana dzierżawa dla Enterprise Mobility + Security E3 i systemu Windows E5 (lub Microsoft 365 Enterprise E5)
- Aktywne środowisko Microsoft Intune z Intune zarządzanymi urządzeniami z systemem Windows [Azure AD przyłączonymi](/azure/active-directory/devices/concept-azure-ad-join/).

### <a name="conditional-access-policy"></a>Zasady dostępu warunkowego

Po włączeniu integracji Intune Intune automatycznie utworzy klasyczne zasady dostępu warunkowego .CA. Te klasyczne zasady urzędu certyfikacji to warunek wstępny konfigurowania raportów o stanie w celu Intune. Nie należy go usuwać.

> [!NOTE]
> Klasyczne zasady urzędu certyfikacji utworzone przez Intune różnią się od nowoczesnych [zasad dostępu warunkowego](/azure/active-directory/conditional-access/overview/), które są używane do konfigurowania punktów końcowych.

## <a name="device-discovery"></a>Wykrywanie urządzeń

Ułatwia znalezienie niezarządzanych urządzeń połączonych z siecią firmową bez konieczności stosowania dodatkowych urządzeń lub kłopotliwych zmian procesów. Przy użyciu urządzeń dołączonych można znaleźć niezarządzane urządzenia w sieci i ocenić luki w zabezpieczeniach i zagrożenia. Aby uzyskać więcej informacji, zobacz [Odnajdywanie urządzeń](device-discovery.md).

> [!NOTE]
> Zawsze można stosować filtry, aby wykluczyć urządzenia niezarządzane z listy spisu urządzeń. Możesz również użyć kolumny stanu dołączania w zapytaniach interfejsu API, aby odfiltrować urządzenia niezarządzane.

## <a name="preview-features"></a>Funkcje wersji zapoznawczej

Dowiedz się więcej o nowych funkcjach w wersji zapoznawczej usługi Defender for Endpoint. Wypróbuj nadchodzące funkcje, włączając środowisko wersji zapoznawczej.

Będziesz mieć dostęp do nadchodzących funkcji, na które możesz przekazać opinię, aby ulepszyć ogólne środowisko, zanim funkcje będą ogólnie dostępne.

## <a name="download-quarantined-files"></a>Pobieranie plików poddanych kwarantannie

Utwórz kopię zapasową plików poddanych kwarantannie w bezpiecznej i zgodnej lokalizacji, aby można je było pobrać bezpośrednio z kwarantanny. Przycisk **Pobierz plik** będzie zawsze dostępny na stronie pliku. To ustawienie jest domyślnie włączone. [Dowiedz się więcej o wymaganiach](respond-file-alerts.md#download-quarantined-files)

## <a name="related-topics"></a>Tematy pokrewne

- [Aktualizowanie ustawień przechowywania danych](data-retention-settings.md)
- [Konfiguruj powiadomienia o alertach](configure-email-notifications.md)
