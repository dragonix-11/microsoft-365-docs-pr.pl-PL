---
title: Zabezpieczenia poczty e-mail za pomocą Eksploratora zagrożeń w programie Microsoft Defender dla Office 365
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
description: Wyświetlaj i przeszukaj próby wyłudzania informacji z złośliwego oprogramowania.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3ee97c54174fc7aaa2cd6d653dcd9fdd8298376d
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021188"
---
# <a name="email-security-with-threat-explorer-in-microsoft-defender-for-office-365"></a>Zabezpieczenia poczty e-mail za pomocą Eksploratora zagrożeń w programie Microsoft Defender dla Office 365

W tym artykule:

- [Wyświetlanie złośliwego oprogramowania wykrytego w wiadomości e-mail](#view-malware-detected-in-email)
- [Wyświetlanie adresu URL wyłudzania informacji i klikanie danych werdyktu](#view-phishing-url-and-click-verdict-data)
- [Rozpoczynanie automatycznego badania i odpowiedzi](#start-automated-investigation-and-response)

> [!NOTE]
> Jest to część 3-articleowej serii w Eksploratorze zagrożeń **(Eksploratorze),** zabezpieczeniach poczty **e-mail****,** Eksploratorze i wykrywaniu w czasie rzeczywistym (takich jak różnice między narzędziami i uprawnienia potrzebne do ich obsługi). Pozostałe dwa artykuły z tej serii to Wyszukiwania [](threat-hunting-in-threat-explorer.md) zagrożeń w Eksploratorze zagrożeń i w Eksploratorze zagrożeń oraz [Wykrywania w czasie rzeczywistym](real-time-detections.md).

W tym artykule wyjaśniono, jak wyświetlać i badać próby wyłudzania informacji i złośliwego oprogramowania wykryte w wiadomościach e-mail za pomocą Microsoft 365 zabezpieczeń.

**Dotyczy:**

- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

## <a name="view-malware-detected-in-email"></a>Wyświetlanie złośliwego oprogramowania wykrytego w wiadomości e-mail

Aby wyświetlić informacje o złośliwym oprogramowaniu wykryte w wiadomościach e-mail Microsoft 365 technologii, [**\>**](threat-explorer-views.md#email--malware) użyj widoku Email Malware w Eksploratorze (lub wykryć w czasie rzeczywistym). Malware is the default view, so it might be selected as soon as you open Explorer.

1. W portalu Microsoft 365 Defender pod <https://security.microsoft.com>adresem , przejdź do opcji Współpracy & e-mail, **a** następnie wybierz pozycję **Wykrywanie** **Eksploratora lub W czasie rzeczywistym**. Aby przejść bezpośrednio do strony, użyj lub <https://security.microsoft.com/threatexplorer> <https://security.microsoft.com/realtimereports>.

   W tym przykładzie użyto **Eksploratora**.

   W tym miejscu rozpocznij od widoku, wybierz określony okres do przejrzenia (w razie potrzeby) i skoncentruj się na filtrach, zgodnie z oknie [Eksploratora](threat-hunting-in-threat-explorer.md#threat-explorer-walk-through).

2. Na liście **rozwijanej** Widok sprawdź, czy jest **wybrana opcja Wyślij** \> wiadomość e-mail **do** złośliwego oprogramowania.

3. Kliknij **pozycję Nadawca**, a następnie **z** \> listy **rozwijanej wybierz** pozycję Technologia wykrywania podstawowego.

   :::image type="content" source="../../media/exploreremailmalwaredetectiontech-newimg.png" alt-text="technologii wykrywania złośliwego oprogramowania.":::

   Technologie wykrywania są teraz dostępne jako filtry raportu.

4. Wybierz opcję, a następnie kliknij pozycję **Odśwież** , aby zastosować ten filtr (nie odświeżaj okna przeglądarki).

   :::image type="content" source="../../media/exploreremailmalwaredetectiontech2-new.png" alt-text="wybranej technologii wykrywania.":::

   Raport zostanie odświeżony w celu pokazania wyników wykrytych w wiadomościach e-mail przez złośliwe oprogramowanie przy użyciu wybranej opcji technologii. Tutaj możesz przeprowadzić dalszą analizę.

### <a name="report-a-message-as-clean-in-explorer"></a>Zgłaszanie wiadomości jako czystej w Eksploratorze

Możesz użyć **opcji Oczyszczanie** raportu w Eksploratorze, aby zgłosić wiadomość jako fałszywie dodatnią. 

1. W portalu Microsoft 365 Defender przejdź do eksploratora poczty e-mail & **współpracy** \> **, a** następnie z listy rozwijanej Widok sprawdź, czy jest wybrana opcja **Phish**.

2. Sprawdź, czy jesteś na karcie Poczta  e-mail, a następnie z listy zgłoszonych wiadomości wybierz tę, która chcesz zgłosić jako czystą. 

3. Kliknij **pozycję** Akcje, aby rozwinąć listę opcji.

4. Przewiń w dół listę opcji, aby przejść do sekcji **Rozpocznij nowe przesyłanie** , a następnie wybierz pozycję **Wyczyść raport**. Zostanie wyświetlone wysuw.

   > [!div class="mx-imgBorder"]
   > ![Opcja Oczyszczanie raportu w Eksploratorze.](../../media/report-clean-option-explorer.png) 

5. Przesuń suwak do przycisku **Wł**. Z listy rozwijanej określ, przez ile dni wiadomość ma zostać usunięta, dodaj notatkę w razie potrzeby, a następnie wybierz pozycję **Prześlij**. 

## <a name="view-phishing-url-and-click-verdict-data"></a>Wyświetlanie adresu URL wyłudzania informacji i klikanie danych werdyktu

Próby wyłudzenia informacji możesz wyświetlić za pomocą adresów URL w wiadomościach e-mail, łącznie z listą adresów URL, które zostały dozwolone, zablokowane i zastąpione. Aby zidentyfikować adresy URL, które zostały klikone, [Sejf skonfigurować](safe-links.md) łącza. Upewnij się, że zasady połączeń [Sejf](set-up-safe-links-policies.md) dotyczące ochrony przed kliknięciami i rejestrowania werdyktów kliknięcia za pomocą linków Sejf kliknięcia.

1. W portalu Microsoft 365 Defender pod <https://security.microsoft.com>adresem , przejdź do opcji Współpracy & e-mail, **a** następnie wybierz pozycję **Wykrywanie** **Eksploratora lub W czasie rzeczywistym**. Aby przejść bezpośrednio do strony, użyj lub <https://security.microsoft.com/threatexplorer> <https://security.microsoft.com/realtimereports>.

   W tym przykładzie użyto **Eksploratora**.

2. Z listy **rozwijanej** Widok wybierz pozycję Wiadomość **e-mail** \> **Phish**.

   > [!div class="mx-imgBorder"]
   > ![Menu Widok w Eksploratorze w kontekście wyłudzania informacji.](../../media/ExplorerViewEmailPhishMenu.png)

3. Kliknij **pozycję Nadawca**, a następnie wybierz pozycję **Adresy URL** \> **Kliknij werdykt** na liście rozwijanej.

4. W wyświetlonych opcjach wybierz jedną lub więcej opcji, takich jak **Zablokowane i Zablokuj** **zastąpione, a** następnie kliknij pozycję **Odśwież (nie** odśwież okna przeglądarki).

    :::image type="content" source="../../media/threatexploreremailphishclickverdict-new.png" alt-text="Adresy URL i klikanie werdyktów.":::

   Raport zostanie odświeżony w celu pokazania dwóch różnych tabel adresów URL na karcie **adresy** URL w obszarze raportu:

   - **Najważniejsze adresy URL to** adresy URL w filtrowanych wiadomościach, a dla każdego adresu URL są liczone akcje dostarczania wiadomości e-mail. W widoku wiadomości e-mail Phish ta lista zawiera zwykle wiarygodne adresy URL. Atakujący zawierają w wiadomościach dobre i złe adresy URL służące do prób ich dostarczenia, ale złośliwi linki wyglądają na bardziej interesujące. Tabela adresów URL jest sortowana według łącznej liczby wiadomości e-mail, ale ta kolumna jest ukryta, aby uprościć widok.

   - **Pierwsze kliknięcia** to kliknięte Sejf URL z zawiniętymi linkami, posortowane według łącznej liczby kliknięć. Ta kolumna również nie jest wyświetlana, aby uprościć widok. Łączna liczba według kolumn wskazuje liczbę Sejf kliknij liczbę werdyktów dla każdego klikowego adresu URL. W widoku wiadomości e-mail Wyłudzy są to zazwyczaj podejrzane lub złośliwe adresy URL. Widok może jednak zawierać adresy URL, które nie są zagrożenia, ale znajdują się w wiadomościach wyłudzeniowych. Kliknięcia adresu URL nieopisanych linków nie są wyświetlane w tym miejscu.

   W obu tabelach adresów URL są wyświetlane najważniejsze adresy URL w wiadomościach e-mail wyłudzających informacje według akcji dostarczenia i lokalizacji. W tabelach są wyświetlane kliknięcia adresów URL, które zostały zablokowane lub odwiedzone pomimo ostrzeżenia, dzięki czemu można zobaczyć, jakie potencjalne złe linki zostały przedstawione użytkownikom i które kliknął. Tutaj możesz przeprowadzić dalszą analizę. Poniżej wykresu można na przykład zobaczyć górne adresy URL wiadomości e-mail, które zostały zablokowane w środowisku organizacji.

   > [!div class="mx-imgBorder"]
   > ![Adresy URL Eksploratora, które zostały zablokowane.](../../media/ExplorerPhishClickVerdictURLs.png)

   Wybierz adres URL, aby wyświetlić bardziej szczegółowe informacje.

   > [!NOTE]
   > W oknie dialogowym Wysuw adresu URL filtrowanie wiadomości e-mail zostanie usunięte w celu pokazania pełnego widoku informacji o ekspozycji adresu URL w Twoim środowisku. To umożliwia filtrowanie pod adresem e-mail, dla których martwi Cię Eksplorator, znajdowanie konkretnych adresów URL, które mogą być zagrożenia, a następnie rozszerzenie rozumienia informacji o narażeniu na adresy URL w Twoim środowisku (za pośrednictwem okna dialogowego szczegółów adresu URL) bez konieczności dodawania filtrów adresów URL do samego widoku Eksploratora.

### <a name="interpretation-of-click-verdicts"></a>Interpretacja werdyktów kliknięcia

W menu wysuwanych wiadomości e-mail lub adresów URL, górnych kliknięciach i w naszych środowiskoch filtrowania zobaczysz różne wartości werdyktów kliknięć:

- **Brak:** Nie można przechwycić werdyktu adresu URL. Być może użytkownik kliknął adres URL.
- **Dozwolone:** Użytkownik mógł przejść do adresu URL.
- **Zablokowane:** Użytkownikowi zablokowano dostęp do adresu URL.
- **Oczekiwanie na werdykt:** Użytkownikowi została przedstawiona strona oczekiwania na detonację.
- **Zablokowane zastąpione:** Użytkownikowi zablokowano dostęp bezpośrednio do adresu URL. Jednak użytkownik overrode the block to navigate to the URL.
- **Oczekiwanie na pominięcie werdyktu:** Użytkownik został zaprezentowany na stronie detonacji. Jednak użytkownik nie korzysta z wiadomości, aby uzyskać dostęp do adresu URL.
- **Błąd:** Użytkownik został przedstawiony na stronie błędu lub wystąpił błąd podczas przechwytywania werdyktu.
- **Niepowodzenie:** Podczas przechwytywania werdyktu wystąpił nieznany wyjątek. Być może użytkownik kliknął adres URL.

## <a name="start-automated-investigation-and-response"></a>Rozpoczynanie automatycznego badania i odpowiedzi

> [!NOTE]
> Funkcje automatycznego badania i odpowiedzi są dostępne w programie *Microsoft Defender dla Office 365 Plan 2* i *Office 365 E5*.

[Zautomatyzowane badania i odpowiedzi](automated-investigation-response-office.md) mogą zaoszczędzić czas i nakład pracy zespołowej związanej z operacjami zabezpieczeń, ale mogą pomóc w zbadaniu i ograniczania cyberataków. Oprócz konfigurowania alertów, które mogą wyzwalać podręcznik zabezpieczeń, możesz uruchomić zautomatyzowany proces badania i odpowiedzi z widoku w Eksploratorze. Aby uzyskać szczegółowe informacje, [zobacz Przykład: Administrator zabezpieczeń wyzwala badanie z Eksploratora](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer).

## <a name="other-articles"></a>Inne artykuły

[Badanie wiadomości e-mail za pomocą strony jednostki poczty e-mail](mdo-email-entity-page.md)
