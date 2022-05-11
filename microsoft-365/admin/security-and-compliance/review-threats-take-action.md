---
title: Przejrzyj wykryte zagrożenia i podejmij działania
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid: MET150
description: Dowiedz się, jak przeglądać zagrożenia wykryte przez Program antywirusowy Microsoft Defender i zarządzać nimi na urządzeniach Windows 10.
ms.openlocfilehash: 9b819edc21d6cfcac663c54e15b1a060b2b16fa2
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2022
ms.locfileid: "65319314"
---
# <a name="review-detected-threats-and-take-action"></a>Przejrzyj wykryte zagrożenia i podejmij działania

Po wykryciu złośliwego pliku lub oprogramowania Program antywirusowy Microsoft Defender blokuje go i uniemożliwia jego uruchomienie. Po włączeniu ochrony dostarczanej w chmurze nowo wykryte zagrożenia są dodawane do aparatu antywirusowego i ochrony przed złośliwym kodem, dzięki czemu inne urządzenia i użytkownicy są również chronieni.

Program antywirusowy Microsoft Defender wykrywa i chroni przed następującymi rodzajami zagrożeń:

- Wirusy, złośliwe oprogramowanie i zagrożenia internetowe na urządzeniach
- Próby wyłudzania informacji
- Próby kradzieży danych

Jako specjalista IT/administrator możesz wyświetlać informacje o wykrywaniu zagrożeń na [Windows 10 urządzeniach zarejestrowanych w Intune](/mem/intune/enrollment/device-enrollment) w Centrum administracyjne platformy Microsoft 365. Zobaczysz podsumowanie informacji, takich jak:

- Ile urządzeń wymaga ochrony antywirusowej
- Ile urządzeń nie jest zgodnych z zasadami zabezpieczeń
- Ile zagrożeń jest obecnie aktywnych, zminimalizowanych lub rozwiązanych

Istnieje kilka opcji wyświetlania określonych informacji na temat wykrywania zagrożeń i urządzeń:

- Strona **Aktywne urządzenia** w <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a>. Zobacz [Zarządzanie wykrywaniem zagrożeń na stronie Aktywne urządzenia](#manage-threat-detections-on-the-active-devices-page) w tym artykule.
- Strona **Aktywne zagrożenia** w <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a>. Zobacz [Zarządzanie wykrywaniem zagrożeń na stronie Aktywne zagrożenia](#manage-threat-detections-on-the-active-threats-page) w tym artykule.
- Strona **Program antywirusowy** w <a href="https://go.microsoft.com/fwlink/p/?linkid=2150463" target="_blank">Microsoft Endpoint Manager</a>. Zobacz [Zarządzanie wykrywaniem zagrożeń w Microsoft Endpoint Manager](#manage-threat-detections-in-microsoft-endpoint-manager) w tym artykule.

Aby dowiedzieć się więcej, zobacz [Threats detected by Program antywirusowy Microsoft Defender (Zagrożenia wykryte przez Program antywirusowy Microsoft Defender](threats-detected-defender-av.md)).

## <a name="manage-threat-detections-on-the-active-devices-page"></a>Zarządzanie wykrywaniem zagrożeń na stronie **Aktywne urządzenia**

Poniższa procedura dotyczy klientów, którzy mają Microsoft 365 Business Premium.

1. Przejdź do Centrum administracyjne platformy Microsoft 365 i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> zaloguj się.

2. Na stronie nawigacji wybierz pozycję **UrządzeniaAktywne** >  urządzenia. Zostanie wyświetlona lista aktywnych urządzeń i szczegółów, takich jak stan ochrony, stan ochrony antywirusowej (AV) i liczba wykrytych aktywnych zagrożeń.

3. Wybierz urządzenie, aby wyświetlić więcej szczegółów dotyczących tego urządzenia i dostępnych akcji. Zostanie otwarte okno wysuwane z zaleceniami i dostępnymi akcjami, takimi jak **zasady aktualizacji**, **aktualizacja oprogramowania antywirusowego**, **szybkie skanowanie przebiegu**, **pełne skanowanie** i inne.

## <a name="manage-threat-detections-on-the-active-threats-page"></a>Zarządzanie wykrywaniem zagrożeń na stronie **Aktywne zagrożenia**

Poniższa procedura dotyczy klientów, którzy mają Microsoft 365 Business Premium. [Windows 10 urządzenia muszą być zabezpieczone](../setup/secure-win-10-pcs.md) i [zarejestrowane w Intune](/mem/intune/enrollment/windows-enrollment-methods).

> [!NOTE]
> Strona karta **Program antywirusowy Microsoft Defender** i **aktywne zagrożenia** są wdrażane etapami, więc możesz nie mieć do nich natychmiastowego dostępu.

1. Przejdź do Centrum administracyjne platformy Microsoft 365 i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> zaloguj się.

2. Na karcie **Program antywirusowy Microsoft Defender** wybierz pozycję **Wyświetl aktywne zagrożenia**. (Alternatywnie w okienku nawigacji wybierz pozycję **Kondycja** >  **Zagrożenia & program antywirusowy**).

3. Na stronie **Aktywne zagrożenia** wybierz wykryte zagrożenie, aby dowiedzieć się więcej na jego temat. Zostanie otwarte okno wysuwane ze szczegółowymi informacjami o tym zagrożeniu, w tym o urządzeniach, których dotyczy problem.

4. Na wysuwnym okienku wybierz urządzenie, aby wyświetlić dostępne akcje, takie jak **zasady aktualizacji**, **aktualizowanie oprogramowania antywirusowego**, **szybkie skanowanie** i nie tylko.

## <a name="actions-you-can-take"></a>Akcje, które można wykonać

Podczas wyświetlania szczegółów dotyczących określonych zagrożeń lub urządzeń zobaczysz zalecenia i co najmniej jedną akcję, którą możesz wykonać. W poniższej tabeli opisano akcje, które mogą zostać wyświetlone.<br><br>

| Akcja | Opis |
|--|--|
| Konfigurowanie ochrony | Należy skonfigurować zasady ochrony przed zagrożeniami. Wybierz link, aby przejść do strony konfiguracji zasad.<br><br>Potrzebujesz pomocy? Zobacz [Zarządzanie zabezpieczeniami urządzeń przy użyciu zasad zabezpieczeń punktu końcowego w Microsoft Intune](/mem/intune/protect/endpoint-security-policy). |
| Aktualizowanie zasad | Należy zaktualizować lub skonfigurować oprogramowanie antywirusowe i zasady ochrony w czasie rzeczywistym. Wybierz link, aby przejść do strony konfiguracji zasad.<br><br>Potrzebujesz pomocy? Zobacz [Zarządzanie zabezpieczeniami urządzeń przy użyciu zasad zabezpieczeń punktu końcowego w Microsoft Intune](/mem/intune/protect/endpoint-security-policy). |
| Uruchamianie szybkiego skanowania | Uruchamia szybkie skanowanie antywirusowe na urządzeniu, koncentrując się na typowych lokalizacjach, w których może być zarejestrowane złośliwe oprogramowanie, takich jak klucze rejestru i znane Windows folderów startowych. |
| Uruchamianie pełnego skanowania | Uruchamia pełne skanowanie antywirusowe na urządzeniu, koncentrując się na typowych lokalizacjach, w których może być zarejestrowane złośliwe oprogramowanie, w tym na każdym pliku i folderze na urządzeniu. Wyniki są wysyłane do [Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager). |
| Aktualizowanie programu antywirusowego | Wymaga, aby urządzenie pobierało [aktualizacje analizy zabezpieczeń](https://go.microsoft.com/fwlink/?linkid=2149926) dla ochrony antywirusowej i ochrony przed złośliwym kodem. |
| Ponowne uruchamianie urządzenia | Wymusza ponowne uruchomienie urządzenia Windows 10 w ciągu pięciu minut.<br><br>**WAŻNE:** Właściciel lub użytkownik urządzenia nie jest automatycznie powiadamiany o ponownym uruchomieniu i może utracić niezapisaną pracę. |

## <a name="manage-threat-detections-in-microsoft-endpoint-manager"></a>Zarządzanie wykrywaniem zagrożeń w Microsoft Endpoint Manager

Za pomocą Microsoft Endpoint Manager można zarządzać wykrywaniem zagrożeń. Windows 10 urządzenia muszą być [zarejestrowane w Intune](/mem/intune/enrollment/windows-enrollment-methods) (część Microsoft Endpoint Manager).

1. Przejdź do centrum administracyjnego Microsoft Endpoint Manager pod adresem <a href="https://go.microsoft.com/fwlink/p/?linkid=2150463" target="_blank">https://endpoint.microsoft.com</a> i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Zabezpieczenia punktu końcowego**.

3. W obszarze **Zarządzanie** wybierz pozycję **Program antywirusowy**. Zobaczysz kilka kart, takich jak **Podsumowanie**, **Windows 10 punkty końcowe w złej kondycji** i **Windows 10 wykryte złośliwe oprogramowanie**.

4. Przejrzyj informacje na dostępnych kartach, a następnie wykonaj wszelkie wymagane akcje.

Załóżmy na przykład, że urządzenia są wymienione na karcie **Windows 10 wykrytego złośliwego oprogramowania**. Po wybraniu urządzenia będą dostępne pewne akcje, takie jak **ponowne uruchamianie**, **szybkie skanowanie**, **pełne skanowanie**, **synchronizacja** lub **aktualizowanie sygnatur**. Wybierz akcję dla tego urządzenia.

W poniższej tabeli opisano akcje, które mogą być widoczne w Microsoft Endpoint Manager.<br><br>

| Akcja | Opis |
|--|--|
| Uruchom ponownie | Wymusza ponowne uruchomienie urządzenia Windows 10 w ciągu pięciu minut.<br><br>**WAŻNE:** Właściciel lub użytkownik urządzenia nie jest automatycznie powiadamiany o ponownym uruchomieniu i może utracić niezapisaną pracę. |
| Szybkie skanowanie | Uruchamia szybkie skanowanie antywirusowe na urządzeniu, koncentrując się na typowych lokalizacjach, w których może być zarejestrowane złośliwe oprogramowanie, takich jak klucze rejestru i znane Windows folderów startowych. Wyniki są wysyłane do [Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager). |
| Pełne skanowanie | Uruchamia pełne skanowanie antywirusowe na urządzeniu, koncentrując się na typowych lokalizacjach, w których może być zarejestrowane złośliwe oprogramowanie, w tym na każdym pliku i folderze na urządzeniu. Wyniki są wysyłane do [Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager). |
| Synchronizuj | Wymaga zaewidencjonowania urządzenia przy użyciu Intune (część Microsoft Endpoint Manager). Podczas zaewidencjonowania urządzenia urządzenie otrzymuje wszelkie oczekujące akcje lub zasady przypisane do urządzenia. |
| Aktualizowanie sygnatur | Wymaga, aby urządzenie pobierało [aktualizacje analizy zabezpieczeń](https://go.microsoft.com/fwlink/?linkid=2149926) dla ochrony antywirusowej i ochrony przed złośliwym kodem. |

> [!TIP]
> Aby uzyskać więcej informacji, zobacz [Akcje zdalne dla urządzeń](/mem/intune/protect/endpoint-security-manage-devices#remote-actions-for-devices).

## <a name="how-to-submit-a-file-for-malware-analysis"></a>Jak przesłać plik do analizy złośliwego oprogramowania

Jeśli masz plik, który według Ciebie został pominięty lub niesłusznie sklasyfikowany jako złośliwe oprogramowanie, możesz przesłać ten plik do firmy Microsoft w celu analizy złośliwego oprogramowania. Użytkownicy i administratorzy IT mogą przesłać plik do analizy. Odwiedź stronę [https://www.microsoft.com/wdsi/filesubmission](https://www.microsoft.com/wdsi/filesubmission).

## <a name="see-also"></a>Zobacz też

[Najlepsze rozwiązania dotyczące zabezpieczania Microsoft 365 dla planów biznesowych](../../admin/security-and-compliance/secure-your-business-data.md)

[Omówienie Microsoft Defender dla Firm](../../security/defender-business/mdb-overview.md) (usługa Defender dla firm jest wdrażana dla Microsoft 365 Business Premium klientów od 1 marca 2022 r.)