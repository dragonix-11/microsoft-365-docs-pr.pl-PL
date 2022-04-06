---
title: Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie iOS
description: W tym artykule opisano, Ochrona punktu końcowego w usłudze Microsoft Defender w funkcjach systemu iOS.
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, ios, configure, features, ios
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: c52fac7c5680d8e5f814098410dc2e1993328d2f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476912"
---
# <a name="configure-microsoft-defender-for-endpoint-on-ios-features"></a>Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Usługa Defender for Endpoint w systemie iOS korzysta z połączenia VPN w celu zapewnienia funkcji ochrony sieci Web. Nie jest to zwykły sieci VPN i jest to lokalny/samopętny vpn, który nie przejmuje ruchu poza urządzenie.

## <a name="conditional-access-with-defender-for-endpoint-on-ios"></a>Dostęp warunkowy z usługą Defender dla punktu końcowego w systemie iOS

Ochrona punktu końcowego w usłudze Microsoft Defender w systemie iOS, a także Microsoft Intune i Azure Active Directory umożliwia wymuszanie zasad zgodności urządzeń i dostępu warunkowego na podstawie wyniku ryzyka urządzenia. Defender for Endpoint is a Mobile Threat Defense (MTD) solution that you can deploy to leverage this capability via Intune.

Aby uzyskać więcej informacji o tym, jak skonfigurować dostęp warunkowy za pomocą programu Defender dla punktu końcowego w systemie iOS, zobacz [Defender for Endpoint (](/mem/intune/protect/advanced-threat-protection)Punkt końcowy) i Intune.

### <a name="jailbreak-detection-by-microsoft-defender-for-endpoint"></a>Wykrywanie błędów według Ochrona punktu końcowego w usłudze Microsoft Defender

Ochrona punktu końcowego w usłudze Microsoft Defender ma możliwość wykrywania urządzeń nieza zarządzaniem i zarządzanych, na których nawiązano łamibę. Jeśli urządzenie zostanie wykryte jako najbędsza najbędsza ochrona przed zagrożeniami, zostanie zgłoszone do portalu programu Microsoft 365 Defender i — jeśli dostęp warunkowy jest konfigurowany na podstawie wyniku ryzyka urządzenia — dostęp do danych firmowych zostanie zablokowany.

## <a name="web-protection-and-vpn"></a>Ochrona sieci Web i sieć VPN

Domyślnie program Defender for Endpoint w systemie iOS zawiera i włącza funkcję ochrony sieci Web. [Ochrona sieci Web](web-protection-overview.md) pomaga zabezpieczyć urządzenia przed zagrożeniami internetowymi i chronić użytkowników przed atakami wyłudzających informacje. Pamiętaj, że w ramach ochrony sieci Web są obsługiwane wskaźniki ochrony przed wyłudzaniem informacji i niestandardowe wskaźniki (adresy URL i IP). Filtrowanie zawartości sieci Web nie jest obecnie obsługiwane w systemie iOS.

W celu zapewnienia tej funkcji usługa Defender for Endpoint w systemie iOS używa połączenia VPN. Pamiętaj, że jest to lokalny interfejs VPN i w przeciwieństwie do tradycyjnych sieci VPN ruch sieciowy nie jest wysyłany poza urządzenie.

Gdy ta funkcja jest domyślnie włączona, może być konieczne wyłączenie połączenia VPN w niektórych przypadkach. Na przykład chcesz uruchomić niektóre aplikacje, które nie działają po skonfigurowaniu połączenia VPN. W takich przypadkach możesz wyłączyć połączenie VPN z aplikacji na urządzeniu, korzystając z poniższych kroków:

1. Na urządzeniu z systemem iOS otwórz aplikację sieci **Ustawienia**, kliknij lub naciśnij pozycję **Ogólne**, a następnie pozycję **VPN**.
1. Kliknij lub naciśnij przycisk "i", aby Ochrona punktu końcowego w usłudze Microsoft Defender.
1. Aby wyłączyć sieć **VPN Połączenie na** żądanie.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-vpn-config.png" alt-text="Przycisk przełącznika dla opcji konfiguracji sieci VPN Połączenie na żądanie" lightbox="images/ios-vpn-config.png":::

> [!NOTE]
> Ochrona sieci Web nie będzie dostępna po wyłączeniu połączenia VPN. Aby ponownie włączyć ochronę sieci Web, otwórz aplikację sieci Ochrona punktu końcowego w usłudze Microsoft Defender na urządzeniu i kliknij lub naciśnij pozycję **Uruchom sieć VPN**.

## <a name="co-existence-of-multiple-vpn-profiles"></a>Co-existence of multiple VPN profiles

System Apple iOS nie obsługuje jednoczesnego działania wielu sieci VPN dla całego urządzenia. Na urządzeniu może istnieć wiele profilów VPN, ale tylko jeden z nich może być aktywny jednocześnie.

## <a name="configure-microsoft-defender-for-endpoint-risk-signal-in-app-protection-policy-mam"></a>Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender ryzyka w zasadach ochrony aplikacji

Ochrona punktu końcowego w usłudze Microsoft Defender można skonfigurować do wysyłania sygnałów zagrożeń, które mają być używane w zasadach ochrony aplikacji (APP, znanej również jako MAM) w systemie iOS/iPadOS. Dzięki tej funkcji możesz chronić Ochrona punktu końcowego w usłudze Microsoft Defender firmowych danych także przed nie zarejestrowanymi urządzeniami.

Poniżej przedstawiono kroki konfigurowania zasad ochrony aplikacji Ochrona punktu końcowego w usłudze Microsoft Defender aplikacji:

1. Skonfiguruj połączenie z dzierżawą Microsoft Endpoint Manager, aby Ochrona punktu końcowego w usłudze Microsoft Defender. W [centrum administracyjnym menedżera punktu końcowego firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) przejdź  \> do pozycji Łączniki administracji dzierżawy i **tokeny** \> (**Ochrona punktu końcowego w usłudze Microsoft Defender** w obszarze Międzyplatformowe) lub **Zabezpieczenia punktów końcowych.** \> **Ochrona punktu końcowego w usłudze Microsoft Defender** (w obszarze Konfiguracja) i włącz przełączniki w obszarze Zasady **ochrony aplikacji Ustawienia dla systemu iOS**.
1. Wybierz Zapisz. Powinien zostać wyświetlony **stan połączenia** : Teraz jest ustawiona wartość **Włączono**.
1. Tworzenie zasad ochrony aplikacji:  \> Po zakończeniu konfiguracji łącznika aplikacji Ochrona punktu końcowego w usłudze Microsoft Defender przejdź do zasad grupy **Ochrona aplikacji** aplikacji (w obszarze Zasady), aby utworzyć nowe zasady lub zaktualizować istniejące.
1. Wybierz platformę, **aplikacje, ochronę danych, ustawienia wymagań programu Access** wymagane przez organizację dla Twoich zasad.
1. W **obszarze Warunkowe** \> **warunki** dotyczące urządzenia można znaleźć ustawienie **Maksymalny dozwolony poziom zagrożeń urządzenia**. Wymaga to skonfigurowania ustawienia Niski, Średni, Wysoki lub Zabezpieczony. Dostępne dla Ciebie akcje to Zablokuj **dostęp** lub **Wyczyść dane**. Zanim to ustawienie zostanie wprowadzone, może zostać wyświetlone okno dialogowe z informacjami, aby upewnić się, że masz już skonfigurowanie łącznika. Jeśli łącznik jest już ustawiony, możesz zignorować to okno dialogowe.
1. Zakończ z Zadaniami i zapisz zasady.

Aby uzyskać więcej informacji na temat zasad MAM lub ochrony aplikacji, zobacz [Ustawienia zasad ochrony aplikacji systemu iOS](/mem/intune/apps/app-protection-policy-settings-ios).

### <a name="deploying-microsoft-defender-for-endpoint-for-mam-or-on-unenrolled-devices"></a>Wdrażanie usługi Ochrona punktu końcowego w usłudze Microsoft Defender mam lub na nie zarejestrowanych urządzeniach

Ochrona punktu końcowego w usłudze Microsoft Defender w systemie iOS włącza scenariusz zasad ochrony aplikacji i jest dostępny w sklepie z aplikacjami firmy Apple.

Użytkownicy końcowi powinni zainstalować najnowszą wersję aplikacji bezpośrednio ze sklepu z aplikacjami firmy Apple.

## <a name="privacy-controls"></a>Mechanizmy kontroli prywatności

> [!IMPORTANT]
> Mechanizmy kontroli prywatności Ochrona punktu końcowego w usłudze Microsoft Defender w systemie iOS są w wersji Preview. Poniższe informacje dotyczą wstępnie dzierżawionych produktów, które mogą ulec znacznej modyfikacji przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

### <a name="configure-privacy-in-phish-alert-report"></a>Konfigurowanie prywatności w raporcie alertów wyłudzy

Klienci mogą teraz włączyć kontrolę prywatności dla raportu phish wysłanego przez Ochrona punktu końcowego w usłudze Microsoft Defender w systemie iOS. Dzięki temu nazwa domeny nie będzie wysyłana w ramach alertu o wyłudzy, gdy witryna internetowa o wyłudzy w sieci Web zostanie wykryta i zablokowana przez Ochrona punktu końcowego w usłudze Microsoft Defender.

Aby włączyć prywatność i nie zbierać nazwy domeny w ramach raportu alertu o wyłudzonych danych, należy wykonać poniższe czynności.

1. W [Microsoft Endpoint Manager administracyjnego i](https://go.microsoft.com/fwlink/?linkid=2109431) przejdź do **pozycji Zasady** >  **konfiguracji aplikacjiAppAddZa** >  >  **zarządzania urządzeniami**.
1. Nadaj zasadom nazwę, **Platform > OS/iPadOS**, wybierz typ profilu.
1. Wybierz **Ochrona punktu końcowego w usłudze Microsoft Defender** jako aplikację docelową.
1. In Ustawienia page, select **Use configuration designer** and **add DefenderExcludeURLInReport** as the key and value type as **Boolean**
   - Aby włączyć prywatność bez zbierania nazwy domeny, wprowadź wartość `true` jako i przypisz te zasady użytkownikom. Domyślnie ta wartość jest ustawiona na `false`.
   - W przypadku użytkowników z `true`kluczem ustawionym jako , alert wyłudzywowy nie będzie zawierał informacji o nazwie domeny, gdy złośliwy witryna zostanie wykryta i zablokowana przez program Defender for Endpoint.
1. Kliknij **przycisk Dalej** i przypisz ten profil do urządzeń/użytkowników docelowych.

Włączenie lub wyłączenie powyższych kontrolek prywatności nie ma wpływu na sprawdzanie zgodności urządzenia ani dostęp warunkowy.

## <a name="configure-compliance-policy-against-jailbroken-devices"></a>Konfigurowanie zasad zgodności przed najbędszą najbędszą konfiguracją na urządzeniach z najbęd

Aby chronić dane firmowe przed dostępem do nich na urządzeniach z systemem iOS z zabezpieczeniami jailbroken, zalecamy skonfigurowanie następujących zasad zgodności na Intune.

> [!NOTE]
> Wykrywanie oprogramowania to funkcja, która jest zapewniana przez funkcję Ochrona punktu końcowego w usłudze Microsoft Defender w systemie iOS. Jednak zalecane jest ustawienie tych zasad jako dodatkowej warstwy ochrony przed scenariuszami.

Wykonaj poniższe czynności, aby utworzyć zasady zgodności dotyczące urządzeń z najbędszą najbędszą odpowiedzialności.

1. W [Microsoft Endpoint Manager administracyjnego](https://go.microsoft.com/fwlink/?linkid=2109431) przejdź do strony **Zasady** ->  **dotyczące urządzeńUtworzenie** ->  **zasad**. Wybierz "iOS/iPadOS" jako platformę, a następnie kliknij pozycję **Utwórz**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-jb-policy.png" alt-text="Karta Tworzenie zasad" lightbox="images/ios-jb-policy.png":::

2. Określ nazwę zasad, na przykład "Zasady zgodności dla Użytkownika".
3. Na stronie ustawień zgodności kliknij, aby rozwinąć **sekcję Kondycja urządzenia** , a następnie kliknij **pole Blokuj** na urządzeniach z **najwętszą blokadą** .

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-jb-settings.png" alt-text="Karta Ustawienia zgodności" lightbox="images/ios-jb-settings.png":::

4. W **sekcji Akcje dla niekompilowania** wybierz akcje zgodnie z wymaganiami, a następnie wybierz pozycję **Dalej**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-jb-actions.png" alt-text="Karta Akcje dla niecompliance" lightbox="images/ios-jb-actions.png":::

5. W **sekcji Zadania** wybierz grupy użytkowników, które chcesz uwzględnić dla tych zasad, a następnie wybierz pozycję **Dalej**.
6. W sekcji **Recenzja+Tworzenie** sprawdź, czy wszystkie wprowadzone informacje są poprawne, a następnie wybierz pozycję **Utwórz**.

## <a name="configure-custom-indicators"></a>Konfigurowanie wskaźników niestandardowych

Program Defender for Endpoint w systemie iOS umożliwia administratorom skonfigurowanie wskaźników niestandardowych również na urządzeniach z systemem iOS. Aby uzyskać więcej informacji na temat konfigurowania wskaźników niestandardowych, zobacz [Zarządzanie wskaźnikami](/microsoft-365/security/defender-endpoint/manage-indicators).

> [!NOTE]
> Program Defender for Endpoint w systemie iOS obsługuje tworzenie wskaźników niestandardowych tylko dla adresów IP i adresów URL/domen.

## <a name="configure-option-to-send-in-app-feedback"></a>Konfigurowanie opcji wysyłania opinii w aplikacji 

Klienci mają teraz możliwość skonfigurowania możliwości wysyłania danych zwrotnych do firmy Microsoft za pomocą aplikacji Defender for Endpoint. Dane opinii pomagają firmie Microsoft w ulepszaniu produktów i rozwiązywaniu problemów.

> [!NOTE]
> W przypadku klientów korzystających z chmury dla instytucji rządowych Stanów Zjednoczonych zbieranie danych **opinii jest domyślnie** wyłączone. 

Aby skonfigurować opcję wysyłania danych opinii do firmy Microsoft, należy wykonać następujące czynności:

1. W [Microsoft Endpoint Manager administracyjnego i](https://go.microsoft.com/fwlink/?linkid=2109431) przejdź do **pozycji Zasady** >  **konfiguracji aplikacjiAppAddZa** >  >  **zarządzania urządzeniami**.
1. Nadaj zasadom nazwę, **Platform > OS/iPadOS**, wybierz typ profilu.
1. Wybierz **Ochrona punktu końcowego w usłudze Microsoft Defender** jako aplikację docelową.
1. Na Ustawienia wybierz pozycję Użyj projektanta **konfiguracji** i dodaj **defenderSendFeedback** jako klucz i typ wartości jako wartość **logiczną**
   - Aby usunąć możliwość wysyłania opinii przez użytkowników końcowych, `false` ustaw wartość zasad i przypisz je użytkownikom. Domyślnie ta wartość jest ustawiona na `true`. W przypadku klientów z instytucji rządowych w Usa wartość domyślna to "fałsz".
   - Dla użytkowników z `true`kluczem ustawionym jako , dostępna będzie opcja wysłania danych opinii do firmy Microsoft w aplikacji (Menu > Pomoc & Opinie > Wyślij opinię do firmy Microsoft)
1. Kliknij **przycisk Dalej** i przypisz ten profil do urządzeń/użytkowników docelowych.


## <a name="report-unsafe-site"></a>Zgłoś niebezpieczną witrynę

Witryny wyłudzujące informacje spersonifikują zaufane witryny internetowe w celu uzyskania informacji osobistych lub finansowych. Odwiedź stronę [Opinie na temat ochrony sieci](https://www.microsoft.com/wdsi/filesubmission/exploitguard/networkprotection) , jeśli chcesz zgłosić witrynę internetową, która może być witryną wyłudzającą informacje.
