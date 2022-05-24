---
title: Zabezpieczenia poczty e-mail za pomocą Eksploratora zagrożeń w Ochrona usługi Office 365 w usłudze Microsoft Defender
f1.keywords:
- NOCSH
ms.author: dansimp
author: MSFTTracyp
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 05/05/2021
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Wyświetlanie i badanie prób wyłudzania informacji o złośliwym oprogramowaniu.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 637e387ca457c9795892791a1a6d9326107fc6fb
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648200"
---
# <a name="email-security-with-threat-explorer-in-microsoft-defender-for-office-365"></a>Zabezpieczenia poczty e-mail za pomocą Eksploratora zagrożeń w Ochrona usługi Office 365 w usłudze Microsoft Defender

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy:**
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W tym artykule:

- [Wyświetlanie złośliwego oprogramowania wykrytego w wiadomości e-mail](#view-malware-detected-in-email)
- [Wyświetl adres URL wyłudzania informacji i kliknij dane werdyktu](#view-phishing-url-and-click-verdict-data)
- [Rozpoczynanie zautomatyzowanego badania i reagowania](#start-automated-investigation-and-response)

> [!NOTE]
> Jest to część **serii 3 artykułów** dotyczących **Eksploratora zagrożeń (Eksplorator),** **zabezpieczeń poczty e-mail** oraz **wykrywania Eksploratora i czasu rzeczywistego** (takich jak różnice między narzędziami i uprawnienia wymagane do ich obsługi). Pozostałe dwa artykuły z tej serii to [wyszukiwanie zagrożeń w Eksploratorze zagrożeń](threat-hunting-in-threat-explorer.md) i [Eksploratorze zagrożeń oraz wykrywanie w czasie rzeczywistym](real-time-detections.md).

W tym artykule wyjaśniono, jak wyświetlać i badać złośliwe oprogramowanie oraz próby wyłudzania informacji wykryte w wiadomościach e-mail za pomocą funkcji zabezpieczeń Microsoft 365.

## <a name="view-malware-detected-in-email"></a>Wyświetlanie złośliwego oprogramowania wykrytego w wiadomości e-mail

Aby wyświetlić złośliwe oprogramowanie wykryte w wiadomościach e-mail posortowanych według technologii Microsoft 365, użyj widoku [**Złośliwe oprogramowanie poczty e-mail \>**](threat-explorer-views.md#email--malware) Eksploratora (lub wykrywania w czasie rzeczywistym). Złośliwe oprogramowanie jest widokiem domyślnym, więc może zostać wybrane natychmiast po otwarciu Eksploratora.

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do pozycji **Poczta e-mail & współpracy**, a następnie wybierz pozycję **Eksplorator** lub **Wykrywanie w czasie rzeczywistym**. Aby przejść bezpośrednio do strony, użyj polecenia <https://security.microsoft.com/threatexplorer> lub <https://security.microsoft.com/realtimereports>.

   W tym **przykładzie użyto Eksploratora**.

   W tym miejscu zacznij od widoku, wybierz określony przedział czasu do zbadania (w razie potrzeby) i skoncentruj filtry zgodnie z [przewodnikiem Eksplorator](threat-hunting-in-threat-explorer.md#threat-explorer-walk-through).

2. Na liście rozwijanej **Widok** sprawdź, czy wybrano **opcję Złośliwe oprogramowanie poczty e-mail**\>.

3. Kliknij pozycję **Nadawca**, a następnie wybierz pozycję **Technologia wykrywania** **podstawowego** \> na liście rozwijanej.

   :::image type="content" source="../../media/exploreremailmalwaredetectiontech-newimg.png" alt-text="Technologia wykrywania złośliwego oprogramowania" lightbox="../../media/exploreremailmalwaredetectiontech-newimg.png":::

   Technologie wykrywania są teraz dostępne jako filtry raportu.

4. Wybierz opcję, a następnie kliknij przycisk **Odśwież** , aby zastosować ten filtr (nie odświeżaj okna przeglądarki).

   :::image type="content" source="../../media/exploreremailmalwaredetectiontech2-new.png" alt-text="wybrana technologia wykrywania" lightbox="../../media/exploreremailmalwaredetectiontech2-new.png":::

   Raport zostanie odświeżony w celu wyświetlenia wyników wykrytych przez złośliwe oprogramowanie w wiadomości e-mail przy użyciu wybranej opcji technologii. W tym miejscu możesz przeprowadzić dalszą analizę.

### <a name="report-a-message-as-clean-in-explorer"></a>Zgłoś komunikat jako czysty w Eksploratorze

Możesz użyć opcji **Wyczyść raport** w Eksploratorze, aby zgłosić komunikat jako fałszywie dodatni. 

1. W portalu Microsoft 365 Defender przejdź do **Eksploratora** współpracy \> **& poczty e-mail**, a następnie na liście rozwijanej Widok sprawdź, czy wybrano pozycję **Phish**.

2. Sprawdź, czy jesteś na karcie **Poczta e-mail** , a następnie z listy zgłoszonych wiadomości wybierz tę, którą chcesz zgłosić jako czystą. 

3. Kliknij pozycję **Akcje** , aby rozwinąć listę opcji.

4. Przewiń listę opcji w dół, aby przejść do sekcji **Rozpocznij nowe przesyłanie** , a następnie wybierz pozycję **Raport wyczyść**. Zostanie wyświetlone okno wysuwane.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/report-clean-option-explorer.png" alt-text="Opcja Czyszczenie raportu w Eksploratorze" lightbox="../../media/report-clean-option-explorer.png":::

5. Przełącz suwak na **Wł**. Z listy rozwijanej określ liczbę dni, przez które komunikat ma zostać usunięty, dodaj notatkę w razie potrzeby, a następnie wybierz pozycję **Prześlij**. 

## <a name="view-phishing-url-and-click-verdict-data"></a>Wyświetl adres URL wyłudzania informacji i kliknij dane werdyktu

Próby wyłudzania informacji można wyświetlać za pośrednictwem adresów URL w wiadomości e-mail, w tym listę dozwolonych, zablokowanych i przesłoniętych adresów URL. Aby zidentyfikować adresy URL, które zostały klikniętych, [Sejf Łącza](safe-links.md) muszą być skonfigurowane. Upewnij się, że skonfigurowano [zasady linków Sejf](set-up-safe-links-policies.md) na potrzeby ochrony przed kliknięciami i rejestrowania werdyktów dotyczących kliknięć za pomocą linków Sejf.

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do pozycji **Poczta e-mail & współpracy**, a następnie wybierz pozycję **Eksplorator** lub **Wykrywanie w czasie rzeczywistym**. Aby przejść bezpośrednio do strony, użyj polecenia <https://security.microsoft.com/threatexplorer> lub <https://security.microsoft.com/realtimereports>.

   W tym **przykładzie użyto Eksploratora**.

2. Na liście rozwijanej **Widok** wybierz pozycję **Poczta e-mail** \> **Phish**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerViewEmailPhishMenu.png" alt-text="Menu Widok dla Eksploratora w kontekście wyłudzania informacji" lightbox="../../media/ExplorerViewEmailPhishMenu.png":::

3. Kliknij **pozycję Nadawca**, a następnie wybierz pozycję **Adresy URL** \> **Kliknij werdykt** na liście rozwijanej.

4. W wyświetlonych opcjach wybierz co najmniej jedną opcję, taką jak **Zablokowane** i **Przesłonięte blokuj**, a następnie kliknij przycisk **Odśwież** (nie odświeżaj okna przeglądarki).

    :::image type="content" source="../../media/threatexploreremailphishclickverdict-new.png" alt-text="Adresy URL i werdykty kliknięcia" lightbox="../../media/threatexploreremailphishclickverdict-new.png":::

   Raport zostanie odświeżony, aby wyświetlić dwie różne tabele adresów URL na karcie **Adresy URL** w raporcie:

   - **Najważniejsze adresy URL** to adresy URL w odfiltrowanych wiadomościach oraz liczba akcji dostarczania wiadomości e-mail dla każdego adresu URL. W widoku poczty e-mail języka Phish ta lista zwykle zawiera prawidłowe adresy URL. Osoby atakujące zawierają kombinację dobrych i złych adresów URL w swoich wiadomościach, aby spróbować je dostarczyć, ale sprawiają, że złośliwe linki wyglądają bardziej interesująco. Tabela adresów URL jest sortowana według łącznej liczby wiadomości e-mail, ale ta kolumna jest ukryta, aby uprościć widok.

   - **Najważniejsze kliknięcia** to Sejf klikniętych adresów URL opakowanych łączami posortowanych według łącznej liczby kliknięć. Ta kolumna również nie jest wyświetlana, aby uprościć widok. Łączna liczba według kolumny wskazuje liczbę kliknięć Sejf Linków dla każdego klikniętego adresu URL. W widoku poczty e-mail języka Phish są to zwykle podejrzane lub złośliwe adresy URL. Ale widok może zawierać adresy URL, które nie są zagrożeniami, ale są w wiadomościach phish. Kliknięcia adresu URL nieopakowanych linków nie są tutaj wyświetlane.

   Dwie tabele adresów URL zawierają najważniejsze adresy URL w wiadomościach e-mail wyłudzających informacje według akcji dostarczania i lokalizacji. W tabelach są wyświetlane kliknięcia adresu URL, które zostały zablokowane lub odwiedzone pomimo ostrzeżenia, dzięki czemu można zobaczyć, jakie potencjalne nieprawidłowe linki zostały wyświetlone użytkownikom i które użytkownicy klikną. W tym miejscu możesz przeprowadzić dalszą analizę. Na przykład poniżej wykresu można zobaczyć najważniejsze adresy URL w wiadomościach e-mail, które zostały zablokowane w środowisku organizacji.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerPhishClickVerdictURLs.png" alt-text="Zablokowane adresy URL Eksploratora" lightbox="../../media/ExplorerPhishClickVerdictURLs.png":::

   Wybierz adres URL, aby wyświetlić bardziej szczegółowe informacje.

   > [!NOTE]
   > W oknie dialogowym wysuwanego adresu URL filtrowanie wiadomości e-mail jest usuwane w celu wyświetlenia pełnego widoku ekspozycji adresu URL w środowisku. Dzięki temu można filtrować wiadomości e-mail, których dotyczy problem w Eksploratorze, znaleźć określone adresy URL, które są potencjalnymi zagrożeniami, a następnie rozszerzyć swoją wiedzę na temat ekspozycji adresu URL w środowisku (za pośrednictwem okna dialogowego szczegóły adresu URL) bez konieczności dodawania filtrów adresów URL do samego widoku Eksploratora.

### <a name="interpretation-of-click-verdicts"></a>Interpretacja werdyktów kliknięcia

W wysuwanych adresach e-mail lub adresach URL, kliknięciach górnych i w naszych środowiskach filtrowania zobaczysz różne wartości werdyktu kliknięcia:

- **Brak:** Nie można przechwycić werdyktu dla adresu URL. Użytkownik mógł kliknąć adres URL.
- **Dozwolone:** Użytkownik mógł przejść do adresu URL.
- **Zablokowany:** Użytkownik nie może przejść do adresu URL.
- **Oczekiwanie na werdykt:** Użytkownikowi przedstawiono stronę oczekującą na detonację.
- **Przesłonięte zablokowane:** Użytkownik nie może przejść bezpośrednio do adresu URL. Ale użytkownik przekroczył blok, aby przejść do adresu URL.
- **Oczekiwanie na werdykt zostało pominięte:** Użytkownikowi przedstawiono stronę detonacji. Ale użytkownik przekroczył komunikat, aby uzyskać dostęp do adresu URL.
- **Błąd:** Użytkownikowi przedstawiono stronę błędu lub wystąpił błąd podczas przechwytywania werdyktu.
- **Awarii:** Wystąpił nieznany wyjątek podczas przechwytywania werdyktu. Użytkownik mógł kliknąć adres URL.

## <a name="start-automated-investigation-and-response"></a>Rozpoczynanie zautomatyzowanego badania i reagowania

> [!NOTE]
> Funkcje zautomatyzowanego badania i reagowania są dostępne w *Ochrona usługi Office 365 w usłudze Microsoft Defender planie 2* i *Office 365 E5*.

[Zautomatyzowane badanie i reagowanie](automated-investigation-response-office.md) może zaoszczędzić czas i nakład pracy zespołu ds. operacji zabezpieczeń poświęcony na badanie i ograniczanie cyberataków. Oprócz konfigurowania alertów, które mogą wyzwalać podręcznik zabezpieczeń, możesz rozpocząć zautomatyzowane badanie i proces reagowania z poziomu widoku w Eksploratorze. Aby uzyskać szczegółowe informacje, zobacz [Przykład: Administrator zabezpieczeń wyzwala badanie z Eksploratora](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer).

## <a name="other-articles"></a>Inne artykuły

[Badanie wiadomości e-mail za pomocą strony jednostki poczty e-mail](mdo-email-entity-page.md)
