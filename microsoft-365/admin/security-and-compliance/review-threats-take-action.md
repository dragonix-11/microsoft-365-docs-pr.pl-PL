---
title: Przeglądanie wykrytych zagrożeń i działanie
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
description: Dowiedz się, jak przeglądać zagrożenia wykryte na Program antywirusowy Microsoft Defender i zarządzać nimi na Windows 10 urządzeniach.
ms.openlocfilehash: c836554445f56a9a915885d55a4490c6bb5bd1a9
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2022
ms.locfileid: "64633221"
---
# <a name="review-detected-threats-and-take-action"></a>Przeglądanie wykrytych zagrożeń i działanie

Po wykryciu złośliwego pliku lub oprogramowania program Program antywirusowy Microsoft Defender go i zapobiega jego uruchomieniu. Gdy jest włączona ochrona dostarczana w chmurze, do aparatu antywirusowego i ochrony przed złośliwym oprogramowaniem są dodawane nowo wykryte zagrożenia, dzięki czemu twoi inni urządzenia i użytkownicy są chronieni.

Program antywirusowy Microsoft Defender wykrywa i chroni przed następującymi rodzajami zagrożeń:

- Wirusy, złośliwe oprogramowanie i zagrożenia internetowe na urządzeniach
- Próby wyłudzania informacji
- Próby kradzieży danych

Jeśli jesteś specjalistą IT/administratorem, możesz wyświetlać informacje o wykrywaniu zagrożeń na Windows 10 [urządzeniach](/mem/intune/enrollment/device-enrollment) zarejestrowanych w programie Intune w Centrum administracyjne platformy Microsoft 365. Zobaczysz informacje podsumowujące, takie jak:

- Ile urządzeń wymaga ochrony antywirusowej
- Ile urządzeń nie jest zgodnych z zasadami zabezpieczeń
- Ile zagrożeń jest obecnie aktywnych, zminimalizowanych lub rozwiązanych

Dostępnych jest kilka opcji wyświetlania określonych informacji na temat wykrywania zagrożeń i urządzeń:

- Strona **Aktywne urządzenia** w <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a>. Zobacz [zarządzanie wykrywaniem zagrożeń na stronie Aktywne urządzenia w](#manage-threat-detections-on-the-active-devices-page) tym artykule.
- Strona **Aktywne zagrożenia** w <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a>. Zobacz [zarządzanie wykrywaniem zagrożeń na stronie Aktywne zagrożenia w](#manage-threat-detections-on-the-active-threats-page) tym artykule.
- Strona **oprogramowania antywirusowego** w <a href="https://go.microsoft.com/fwlink/p/?linkid=2150463" target="_blank">Microsoft Endpoint Manager</a>. Zobacz [zarządzanie wykrywaniem zagrożeń w Microsoft Endpoint Manager](#manage-threat-detections-in-microsoft-endpoint-manager) tym artykule.

Aby dowiedzieć się więcej, zobacz [Zagrożenia wykryte przez Program antywirusowy Microsoft Defender](threats-detected-defender-av.md).

## <a name="manage-threat-detections-on-the-active-devices-page"></a>Zarządzanie wykrywaniem zagrożeń na **stronie Aktywne** urządzenia

Następująca procedura dotyczy klientów, którzy mają Microsoft 365 Business Premium.

1. Przejdź do Centrum administracyjne platformy Microsoft 365 i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> zaloguj się.

2. Na stronie nawigacji wybierz pozycję **UrządzeniaAktywowanie** >  urządzeń. Zostanie wyświetlona lista aktywnych urządzeń i szczegóły, takie jak stan ochrony, stan ochrony oprogramowania antywirusowego i liczba wykrytych aktywnych zagrożeń.

3. Wybierz urządzenie, aby wyświetlić więcej szczegółów dotyczących tego urządzenia i dostępnych akcji. Zostanie otwarte menu wysuwu z zaleceniami i dostępnymi akcjami, takimi jak Zasady **aktualizacji, Aktualizuj** oprogramowanie **antywirusowe, Uruchom** szybkie **skanowanie,** **Uruchom pełne** skanowanie i nie tylko.

## <a name="manage-threat-detections-on-the-active-threats-page"></a>Zarządzanie wykrywaniem zagrożeń na **stronie Aktywne zagrożenia**

Następująca procedura dotyczy klientów, którzy mają Microsoft 365 Business Premium. [Windows 10 urządzenia muszą być zabezpieczone i](../setup/secure-win-10-pcs.md) [zarejestrowane w Intune](/mem/intune/enrollment/windows-enrollment-methods).

> [!NOTE]
> Strona **Program antywirusowy Microsoft Defender** i **Aktywne** zagrożenia są rozdawana w fazach, więc możesz nie mieć do nich natychmiastowego dostępu.

1. Przejdź do Centrum administracyjne platformy Microsoft 365 i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> zaloguj się.

2. Na karcie **Program antywirusowy Microsoft Defender** wybierz pozycję **Wyświetl aktywne zagrożenia**. (Alternatywnie w okienku nawigacji wybierz pozycję **Kondycja** >  **Zagrożenia & oprogramowania antywirusowego**).

3. Na stronie **Aktywne zagrożenia** wybierz wykryte zagrożenie, aby dowiedzieć się więcej na jego temat. Zostanie otwarte okno wysuwu ze szczegółami zagrożenia, w tym o urządzeniach, których dotyczy problem.

4. W wysuwanych menu wybierz urządzenie, aby wyświetlić dostępne akcje, takie jak Zasady **aktualizacji, Aktualizuj** oprogramowanie **antywirusowe**, **Uruchom szybkie skanowanie** i nie tylko.

## <a name="actions-you-can-take"></a>Akcje, które można podjąć

Gdy wyświetlasz szczegółowe informacje o konkretnych zagrożeniach lub urządzeniach, zobaczysz zalecenia i co najmniej jedną konkretną konkretną czynów do podjęcia. W poniższej tabeli opisano czynności, które mogą zostać dosyć dosyć.<br><br>

| Akcja | Opis |
|--|--|
| Konfigurowanie ochrony | Konieczne jest skonfigurowanie zasad ochrony przed zagrożeniami. Wybierz link, aby przejść do strony konfiguracji zasad.<br><br>Potrzebujesz pomocy? Zobacz [Zarządzanie zabezpieczeniami urządzeń za pomocą zasad zabezpieczeń punktów końcowych w Microsoft Intune](/mem/intune/protect/endpoint-security-policy). |
| Zasady aktualizacji | Należy zaktualizować lub skonfigurować zasady ochrony w czasie rzeczywistym oraz zasady ochrony w czasie rzeczywistym. Wybierz link, aby przejść do strony konfiguracji zasad.<br><br>Potrzebujesz pomocy? Zobacz [Zarządzanie zabezpieczeniami urządzeń za pomocą zasad zabezpieczeń punktów końcowych w Microsoft Intune](/mem/intune/protect/endpoint-security-policy). |
| Uruchamianie szybkiego skanowania | Uruchamia szybkie skanowanie antywirusowe na urządzeniu, skupiając się na typowych lokalizacjach, w których może być rejestrowane złośliwe oprogramowanie, takie jak klucze rejestru i znane Windows uruchamiania. |
| Uruchom pełne skanowanie | Uruchamia pełne skanowanie antywirusowe na urządzeniu, skupiając się na typowych lokalizacjach, w których może być rejestrowane złośliwe oprogramowanie, i uwzględniając wszystkie pliki i foldery na urządzeniu. Wyniki są wysyłane do [Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager). |
| Aktualizowanie oprogramowania antywirusowego | Wymaga urządzenia do uzyskania aktualizacji [analizy zabezpieczeń w](https://go.microsoft.com/fwlink/?linkid=2149926) celu ochrony przed złośliwym oprogramowaniem i oprogramowaniem antywirusowym. |
| Uruchom ponownie urządzenie | Wymusza ponowne uruchomienie Windows 10 urządzenia w ciągu pięciu minut.<br><br>**WAŻNE:** Właściciel lub użytkownik urządzenia nie jest automatycznie powiadamiany o ponownym uruchomieniu i może utracić niezapisaną pracę. |

## <a name="manage-threat-detections-in-microsoft-endpoint-manager"></a>Zarządzanie wykrywaniem zagrożeń w Microsoft Endpoint Manager

Wykrywanie zagrożeń można Microsoft Endpoint Manager za pomocą funkcji zarządzania zagrożeniami. Windows 10 urządzenia muszą być [zarejestrowane w usłudze Intune](/mem/intune/enrollment/windows-enrollment-methods) (część Microsoft Endpoint Manager).

1. Przejdź do centrum Microsoft Endpoint Manager administracyjnego i <a href="https://go.microsoft.com/fwlink/p/?linkid=2150463" target="_blank">https://endpoint.microsoft.com</a> zaloguj się.

2. W okienku nawigacji wybierz pozycję **Zabezpieczenia punktu końcowego**.

3. W **obszarze Zarządzanie** wybierz pozycję **Oprogramowanie antywirusowe**. Zostanie wyświetlonych kilka kart, takich jak **Podsumowanie,** **Windows 10** punktów końcowych o złej kondycji i Windows 10 **złośliwym oprogramowaniem**.

4. Przejrzyj informacje na dostępnych kartach, a następnie wybierz wymagane działania.

Załóżmy na przykład, że urządzenia znajdują się na **karcie Windows 10 złośliwym** oprogramowaniem. Po wybraniu urządzenia będą dostępne pewne akcje, takie jak Ponowne **uruchomienie, Szybkie** **skanowanie, Pełne** **skanowanie,** **Synchronizuj** lub **Aktualizuj podpisy**. Wybierz akcję dla tego urządzenia.

W poniższej tabeli opisano akcje, które mogą być Microsoft Endpoint Manager.<br><br>

| Akcja | Opis |
|--|--|
| Uruchom ponownie | Wymusza ponowne uruchomienie Windows 10 urządzenia w ciągu pięciu minut.<br><br>**WAŻNE:** Właściciel lub użytkownik urządzenia nie jest automatycznie powiadamiany o ponownym uruchomieniu i może utracić niezapisaną pracę. |
| Szybkie skanowanie | Uruchamia szybkie skanowanie antywirusowe na urządzeniu, skupiając się na typowych lokalizacjach, w których może być rejestrowane złośliwe oprogramowanie, takie jak klucze rejestru i znane Windows uruchamiania. Wyniki są wysyłane do [Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager). |
| Pełne skanowanie | Uruchamia pełne skanowanie antywirusowe na urządzeniu, skupiając się na typowych lokalizacjach, w których może być rejestrowane złośliwe oprogramowanie, i uwzględniając wszystkie pliki i foldery na urządzeniu. Wyniki są wysyłane do [Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager). |
| Synchronizuj | Wymaga urządzenia do sprawdzenia za pomocą Intune (część Microsoft Endpoint Manager). Gdy urządzenie zae testuje, otrzymuje wszystkie oczekujące akcje lub zasady przypisane do urządzenia. |
| Aktualizowanie podpisów | Wymaga urządzenia do uzyskania aktualizacji [analizy zabezpieczeń w](https://go.microsoft.com/fwlink/?linkid=2149926) celu ochrony przed złośliwym oprogramowaniem i oprogramowaniem antywirusowym. |

> [!TIP]
> Aby uzyskać więcej informacji, zobacz [Akcje zdalne dla urządzeń](/mem/intune/protect/endpoint-security-manage-devices#remote-actions-for-devices).

## <a name="how-to-submit-a-file-for-malware-analysis"></a>Jak przesłać plik do analizy złośliwego oprogramowania

Jeśli masz plik, który został uznany za nieodebrany lub niesłusznie sklasyfikowany jako złośliwe oprogramowanie, możesz przesłać go do firmy Microsoft w celu analizy złośliwego oprogramowania. Użytkownicy i administratorzy IT mogą przesłać plik do analizy. Odwiedź [https://www.microsoft.com/wdsi/filesubmission](https://www.microsoft.com/wdsi/filesubmission)stronę .

## <a name="see-also"></a>Zobacz też

[10 najlepszych sposobów zabezpieczania planów Microsoft 365 dla firm](../../admin/security-and-compliance/secure-your-business-data.md)

[Omówienie programu Microsoft Defender dla Firm](../../security/defender-business/mdb-overview.md) (od 1 marca 2022 r. dla klientów usługi Defender Microsoft 365 Business Premium firm)