---
title: Profil urządzenia w portalu zabezpieczeń platformy Microsoft 365
description: Wyświetlanie poziomów ryzyka i ekspozycji dla urządzenia w organizacji. Analizowanie przeszłych i obecnych zagrożeń oraz ochrona urządzenia przy użyciu najnowszych aktualizacji.
keywords: zabezpieczenia, złośliwe oprogramowanie, Microsoft 365, M365, Microsoft 365 Defender, Security Center, Microsoft Defender for Endpoint, Microsoft Defender for Office 365, Microsoft Defender for Identity, strona urządzenia, profil urządzenia, strona komputera, profil komputera
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
ms.author: dansimp
author: martyav
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: 962ec0c5ed6b7d6934678678be9a57ebcbaabc55
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2022
ms.locfileid: "65923439"
---
# <a name="device-profile-page"></a>Strona profilu urządzenia

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


Portal zabezpieczeń platformy Microsoft 365 udostępnia strony profilów urządzeń, dzięki czemu można szybko ocenić kondycję i stan urządzeń w sieci.

> [!IMPORTANT]
> Strona profilu urządzenia może wyglądać nieco inaczej, w zależności od tego, czy urządzenie zostało zarejestrowane w usłudze Microsoft Defender dla punktu końcowego, w usłudze Microsoft Defender for Identity, czy w obu tych przypadkach.

Jeśli urządzenie jest zarejestrowane w usłudze Microsoft Defender for Endpoint, możesz również użyć strony profilu urządzenia do wykonywania niektórych typowych zadań zabezpieczeń.

## <a name="navigating-the-device-profile-page"></a>Nawigowanie po stronie profilu urządzenia

Strona profilu jest podzielona na kilka szerokich sekcji.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-overall.png" alt-text="Strona Profil urządzenia w portalu usługi Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-overall.png":::

Pasek boczny (1) zawiera podstawowe informacje o urządzeniu.

Główny obszar zawartości (2) zawiera karty, które można przełączać, aby wyświetlić różne rodzaje informacji o urządzeniu.

Jeśli urządzenie jest zarejestrowane w usłudze Microsoft Defender for Endpoint, zostanie również wyświetlona lista akcji odpowiedzi (3). Akcje odpowiedzi umożliwiają wykonywanie typowych zadań związanych z zabezpieczeniami.

## <a name="sidebar"></a>Pasku bocznym

Obok głównego obszaru zawartości strony profilu urządzenia znajduje się pasek boczny.

:::image type="content" source="../../media/mtp-device-profile/azure-atp-only-device-sidebar.png" alt-text="Karta Pasek boczny profilu urządzenia w portalu usługi Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/azure-atp-only-device-sidebar.png":::

Na pasku bocznym jest wyświetlana pełna nazwa urządzenia i poziom ekspozycji. Zawiera również kilka ważnych podstawowych informacji w małych podsekcjach, które można przełączać otwarte lub zamknięte, takie jak:

* **Tagi** — dowolna usługa Microsoft Defender dla punktu końcowego, usługa Microsoft Defender for Identity lub tagi niestandardowe skojarzone z urządzeniem. Nie można edytować tagów z usługi Microsoft Defender for Identity.
* **Informacje zabezpieczające** — otwieranie zdarzeń i aktywnych alertów. Urządzenia zarejestrowane w usłudze Microsoft Defender dla punktu końcowego będą również wyświetlać poziom narażenia i poziom ryzyka.

> [!TIP]
> Poziom narażenia odnosi się do tego, jak bardzo urządzenie jest zgodne z zaleceniami dotyczącymi zabezpieczeń, podczas gdy poziom ryzyka jest obliczany na podstawie wielu czynników, w tym typów i ważności aktywnych alertów.

* **Szczegóły urządzenia** — domena, system operacyjny, sygnatura czasowa pierwszego wyświetleń urządzenia, adresy IP, zasoby. Urządzenia zarejestrowane w usłudze Microsoft Defender dla punktu końcowego również wyświetlają stan kondycji. Na urządzeniach zarejestrowanych w usłudze Microsoft Defender for Identity będzie wyświetlana nazwa SAM i sygnatura czasowa pierwszego utworzenia urządzenia.
* **Aktywność sieciowa** — znaczniki czasu po raz pierwszy i ostatni raz urządzenie było widoczne w sieci.
* **Dane katalogu** (*tylko dla urządzeń zarejestrowanych w usłudze Microsoft Defender for Identity*) — flagi funkcji [UAC](/windows/security/identity-protection/user-account-control/user-account-control-overview) , [nazwy SPN](/windows/win32/ad/service-principal-names) i członkostwo w grupach.

## <a name="response-actions"></a>Akcje odpowiedzi

Akcje reagowania oferują szybki sposób na obronę przed zagrożeniami i analizowanie ich.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-long-action-bar.png" alt-text="Pasek akcji profilu urządzenia w portalu usługi Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-long-action-bar.png":::

> [!IMPORTANT]
> * [Akcje odpowiedzi](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts) są dostępne tylko wtedy, gdy urządzenie jest zarejestrowane w usłudze Microsoft Defender for Endpoint.
> * Urządzenia zarejestrowane w usłudze Microsoft Defender for Endpoint mogą wyświetlać różne liczby akcji odpowiedzi na podstawie systemu operacyjnego i numeru wersji urządzenia.

Akcje dostępne na stronie profilu urządzenia obejmują:

* **Zarządzanie tagami** — aktualizuje tagi niestandardowe zastosowane do tego urządzenia.
* **Izolowanie urządzenia** — izoluje urządzenie od sieci organizacji przy jednoczesnym zachowaniu połączenia z usługą Microsoft Defender for Endpoint. Możesz zezwolić na uruchamianie aplikacji Outlook, Teams i Skype dla firm, gdy urządzenie jest izolowane do celów komunikacyjnych.
* **Centrum akcji** — wyświetl stan przesłanych akcji. Dostępne tylko wtedy, gdy wybrano już inną akcję.
* **Ograniczanie wykonywania aplikacji** — uniemożliwia uruchamianie aplikacji, które nie są podpisane przez firmę Microsoft.
* **Uruchom skanowanie antywirusowe** — aktualizuje definicje programu antywirusowego Windows Defender i natychmiast uruchamia skanowanie antywirusowe. Wybierz opcję szybkiego skanowania lub pełnego skanowania.
* **Zbieranie pakietu badania** — zbiera informacje o urządzeniu. Po zakończeniu badania możesz je pobrać.
* **Inicjowanie sesji odpowiedzi na żywo** — ładuje zdalną powłokę na urządzeniu [w celu przeprowadzenia szczegółowych badań zabezpieczeń](/microsoft-365/security/defender-endpoint/live-response).
* **Inicjowanie zautomatyzowanego badania** — automatycznie [bada i koryguje zagrożenia](../office-365-security/office-365-air.md). Chociaż możesz ręcznie wyzwolić automatyczne badania, aby uruchomić je z tej strony, [niektóre zasady alertów](../../compliance/alert-policies.md#default-alert-policies) wywołują automatyczne badania samodzielnie.
* **Centrum akcji** — wyświetla informacje o aktualnie uruchomionych akcjach odpowiedzi.

## <a name="tabs-section"></a>Sekcja tabulatorów

Karty profilu urządzenia umożliwiają przełączanie się przez przegląd szczegółów zabezpieczeń dotyczących urządzenia oraz tabel zawierających listę alertów.

Urządzenia zarejestrowane w usłudze Microsoft Defender dla punktu końcowego będą również wyświetlać karty zawierające oś czasu, listę zaleceń dotyczących zabezpieczeń, spis oprogramowania, listę wykrytych luk w zabezpieczeniach i brakujące bazy danych (aktualizacje zabezpieczeń).

### <a name="overview-tab"></a>Karta Przegląd

Domyślna karta to **Przegląd**. Umożliwia szybkie zapoznanie się z najważniejszym faktem dotyczącym zabezpieczeń urządzenia.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-overview.png" alt-text="Karta Przegląd profilu urządzenia w portalu usługi Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-overview.png":::

W tym miejscu możesz szybko przyjrzeć się aktywnym alertom urządzenia i dowolnym aktualnie zalogowanym użytkownikom.

Jeśli urządzenie jest zarejestrowane w usłudze Microsoft Defender for Endpoint, zobaczysz również poziom ryzyka urządzenia i wszystkie dostępne dane dotyczące ocen zabezpieczeń. W ocenach zabezpieczeń opisano poziom narażenia urządzenia, przedstawiono zalecenia dotyczące zabezpieczeń oraz wymieniono oprogramowanie, którego dotyczy problem, oraz wykryte luki w zabezpieczeniach.

### <a name="alerts-tab"></a>Karta Alerty

Karta **Alerty** zawiera listę alertów, które zostały zgłoszone na urządzeniu, zarówno z usługi Microsoft Defender for Identity, jak i usługi Microsoft Defender for Endpoint.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-alerts.png" alt-text="Karta Alerty profilu urządzenia w portalu usługi Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-alerts.png":::

Możesz dostosować liczbę wyświetlanych elementów, a także kolumny wyświetlane dla każdego elementu. Domyślnym zachowaniem jest wyświetlenie listy trzydziestu elementów na stronę.

Kolumny na tej karcie zawierają informacje o ważności zagrożenia, które wyzwoliło alert, a także o stanie, stanie badania i o tym, do kogo przypisano alert.

Kolumna *jednostek, których dotyczy problem* , odnosi się do urządzenia (jednostki), którego profil jest obecnie przeglądany, oraz innych urządzeń w sieci, których dotyczy problem.

Wybranie elementu z tej listy spowoduje otwarcie wysuwanego elementu zawierającego jeszcze więcej informacji o wybranym alertie.

Tę listę można filtrować według ważności, stanu lub osoby, do których przypisano alert.

### <a name="timeline-tab"></a>Karta Oś czasu

Karta **Oś czasu** zawiera interaktywny, chronologiczny wykres wszystkich zdarzeń zgłoszonych na urządzeniu. Przesuwając wyróżniony obszar wykresu w lewo lub w prawo, można wyświetlać zdarzenia w różnych okresach. Możesz również wybrać niestandardowy zakres dat z menu rozwijanego między wykresem interaktywnym a listą zdarzeń.

Poniżej wykresu znajduje się lista zdarzeń dla wybranego zakresu dat.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-timeline.png" alt-text="Karta Oś czasu profilu urządzenia w portalu usługi Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-timeline.png":::

Liczbę wyświetlanych elementów i kolumny na liście można dostosować. Kolumny domyślne zawierają listę czasu zdarzenia, aktywnego użytkownika, typu akcji, jednostek (procesów) i dodatkowych informacji o zdarzeniu.

Wybranie elementu z tej listy spowoduje otwarcie wysuwanego wykresu jednostek zdarzeń z wyświetlonymi procesami nadrzędnymi i podrzędnymi biorącymi udział w zdarzeniu.

Listę można filtrować według określonego rodzaju zdarzenia. na przykład zdarzenia rejestru lub zdarzenia inteligentnego ekranu.

Listę można również wyeksportować do pliku CSV do pobrania. Chociaż plik nie jest ograniczony liczbą zdarzeń, maksymalny zakres czasu, który można wyeksportować, wynosi siedem dni.

### <a name="security-recommendations-tab"></a>Karta Zalecenia dotyczące zabezpieczeń

Karta **Zalecenia dotyczące zabezpieczeń** zawiera listę akcji, które można wykonać w celu ochrony urządzenia. Wybranie elementu na tej liście spowoduje otwarcie wysuwanego elementu, w którym można uzyskać instrukcje dotyczące sposobu stosowania zalecenia.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-security-recs.png" alt-text="Karta Zalecenia dotyczące zabezpieczeń profilu urządzenia w portalu usługi Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-security-recs.png":::

Podobnie jak w przypadku poprzednich kart, można dostosować liczbę elementów wyświetlanych na stronie, a także kolumny, które są widoczne.

Widok domyślny zawiera kolumny zawierające szczegółowe informacje o rozwiązanych słabych stronach zabezpieczeń, skojarzonym zagrożeniu, powiązanym składniku lub oprogramowaniu dotkniętym zagrożeniem i nie tylko. Elementy można filtrować według stanu zalecenia.

### <a name="software-inventory"></a>Spis oprogramowania

Karta **Spis oprogramowania** zawiera listę oprogramowania zainstalowanego na urządzeniu.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-software-inventory.png" alt-text="Karta Spis oprogramowania dla profilu urządzenia w portalu usługi Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-software-inventory.png":::

W widoku domyślnym jest wyświetlany dostawca oprogramowania, numer zainstalowanej wersji, liczba znanych słabych stron oprogramowania, szczegółowe informacje o zagrożeniach, kod produktu i tagi. Liczbę wyświetlanych elementów i wyświetlane kolumny można dostosować.

Wybranie elementu z tej listy powoduje otwarcie okna wysuwanego zawierającego więcej szczegółów na temat wybranego oprogramowania, a także ścieżkę i sygnaturę czasową ostatniego znalezienia oprogramowania.

Tę listę można filtrować według kodu produktu.

### <a name="discovered-vulnerabilities-tab"></a>Karta Wykryte luki w zabezpieczeniach

Karta **Wykryte luki w zabezpieczeniach** zawiera listę typowych luk w zabezpieczeniach i luk w zabezpieczeniach ,które mogą mieć wpływ na urządzenie.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-discovered-vulnerabilities.png" alt-text="Karta Wykryte luki w zabezpieczeniach profilu urządzenia w portalu usługi Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-discovered-vulnerabilities.png":::

W widoku domyślnym wymieniono ważność CVE, wspólny wskaźnik luk w zabezpieczeniach (CVS), oprogramowanie związane z CVE, kiedy CVE zostało opublikowane, kiedy CVE zostało ostatnio zaktualizowane, oraz zagrożenia związane z CVE.

Podobnie jak w przypadku poprzednich kart, można dostosować liczbę wyświetlanych elementów i widoczne kolumny.

Wybranie elementu z tej listy spowoduje otwarcie wysuwanego elementu opisującego cve.

### <a name="missing-kbs"></a>Brakujące bazy danych

Na karcie **Brakujące bazy danych** są wyświetlane wszystkie aktualizacje firmy Microsoft, które nie zostały jeszcze zastosowane do urządzenia. Przedmiotowe "bazy wiedzy" to [artykuły z bazy wiedzy](https://support.microsoft.com/help/242450/how-to-query-the-microsoft-knowledge-base-by-using-keywords-and-query) , które opisują te aktualizacje; na przykład [KB4551762](https://support.microsoft.com/help/4551762/windows-10-update-kb4551762).

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-missing-kbs.PNG" alt-text="Karta Brakujące bazy danych dla profilu urządzenia w portalu usługi Microsoft 365 Defender" lightbox="../../media/mtp-device-profile/hybrid-device-tab-missing-kbs.PNG":::

Widok domyślny zawiera biuletyn zawierający aktualizacje, wersję systemu operacyjnego, produkty, których dotyczy problem, adresowane cve, numer KB i tagi.

Liczbę elementów wyświetlanych na stronie i kolumny, które są wyświetlane, można dostosować.

Wybranie elementu spowoduje otwarcie wysuwanego elementu, który łączy się z aktualizacją.

## <a name="related-topics"></a>Tematy pokrewne

* [Omówienie usługi Microsoft 365 Defender](microsoft-365-defender.md)
* [Włączanie usługi Microsoft 365 Defender](m365d-enable.md)
* [Badanie jednostek na urządzeniach przy użyciu odpowiedzi na żywo](../defender-endpoint/live-response.md)
* [Automatyczne badanie i reagowanie (AIR) w usłudze Office 365](../office-365-security/office-365-air.md)
