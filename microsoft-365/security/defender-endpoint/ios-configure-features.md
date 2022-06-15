---
title: Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS
description: Opis sposobu wdrażania Ochrona punktu końcowego w usłudze Microsoft Defender w funkcjach iOS.
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
ms.openlocfilehash: 8defbb5d1a72afd13110d3c76a4770e40ac1c469
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2022
ms.locfileid: "66089312"
---
# <a name="configure-microsoft-defender-for-endpoint-on-ios-features"></a>Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Usługa Defender for Endpoint w iOS będzie używać sieci VPN w celu zapewnienia funkcji ochrony sieci Web. Nie jest to zwykła sieć VPN i jest lokalną/samopętlaną siecią VPN, która nie przyjmuje ruchu poza urządzeniem.

## <a name="conditional-access-with-defender-for-endpoint-on-ios"></a>Dostęp warunkowy za pomocą usługi Defender dla punktu końcowego w iOS

Ochrona punktu końcowego w usłudze Microsoft Defender na iOS wraz z Microsoft Intune i Azure Active Directory umożliwia wymuszanie zasad zgodności urządzeń i dostępu warunkowego na podstawie oceny ryzyka urządzenia. Defender for Endpoint to rozwiązanie usługi Mobile Threat Defense (MTD), które można wdrożyć w celu wykorzystania tej możliwości za pośrednictwem Intune.

Aby uzyskać więcej informacji na temat konfigurowania dostępu warunkowego za pomocą usługi Defender for Endpoint na iOS, zobacz [Defender for Endpoint and Intune (Usługa Defender dla punktu końcowego i Intune](/mem/intune/protect/advanced-threat-protection)).

### <a name="jailbreak-detection-by-microsoft-defender-for-endpoint"></a>Wykrywanie jailbreaku przez Ochrona punktu końcowego w usłudze Microsoft Defender

Ochrona punktu końcowego w usłudze Microsoft Defender ma możliwość wykrywania niezarządzanych i zarządzanych urządzeń ze zdjętymi zabezpieczeniami systemu. Jeśli urządzenie zostanie wykryte jako zdjęte z poziomu systemu, alert **wysokiego** ryzyka zostanie zgłoszony do portalu Microsoft 365 Defender, a jeśli dostęp warunkowy zostanie skonfigurowany na podstawie wyniku ryzyka urządzenia, dostęp urządzenia do danych firmowych zostanie zablokowany.

## <a name="web-protection-and-vpn"></a>Ochrona sieci Web i sieć VPN

Domyślnie usługa Defender for Endpoint na iOS obejmuje i włącza funkcję ochrony w Internecie. [Ochrona w Internecie](web-protection-overview.md) pomaga zabezpieczyć urządzenia przed zagrożeniami internetowymi i chronić użytkowników przed atakami wyłudzania informacji. Należy pamiętać, że wskaźniki ochrony przed wyłudzaniem informacji i niestandardowe (adresy URL i adresy IP) są obsługiwane w ramach usługi Web Protection. Filtrowanie zawartości sieci Web nie jest obecnie obsługiwane w iOS.

Usługa Defender for Endpoint w iOS używa sieci VPN w celu zapewnienia tej możliwości. Należy pamiętać, że jest to lokalna sieć VPN i w przeciwieństwie do tradycyjnej sieci VPN ruch sieciowy nie jest wysyłany poza urządzenie.

Mimo że jest domyślnie włączona, mogą wystąpić pewne przypadki, które wymagają wyłączenia sieci VPN. Na przykład chcesz uruchomić niektóre aplikacje, które nie działają po skonfigurowaniu sieci VPN. W takich przypadkach możesz wyłączyć sieć VPN z aplikacji na urządzeniu, wykonując poniższe kroki:

1. Na urządzeniu iOS otwórz aplikację **Ustawienia**, kliknij lub naciśnij pozycję **Ogólne**, a następnie sieć **VPN**.

2. Kliknij lub naciśnij przycisk "i" dla Ochrona punktu końcowego w usłudze Microsoft Defender.

3. Wyłącz **Połączenie na żądanie**, aby wyłączyć sieć VPN. 

   :::image type="content" source="images/ios-vpn-config.png" alt-text="Przycisk przełączania dla konfiguracji sieci VPN Połączenie na żądanie" lightbox="images/ios-vpn-config.png":::

> [!NOTE]
> Usługa Web Protection nie będzie dostępna po wyłączeniu sieci VPN. Aby ponownie włączyć usługę Web Protection, otwórz aplikację Ochrona punktu końcowego w usłudze Microsoft Defender na urządzeniu i kliknij lub naciśnij pozycję **Uruchom sieć VPN**.

## <a name="configure-network-protection"></a>Konfigurowanie ochrony sieci
>[!NOTE] 
>Ochrona sieci w Ochrona punktu końcowego w usłudze Microsoft Defender jest teraz dostępna w publicznej wersji zapoznawczej. Poniższe informacje odnoszą się do wstępnej wersji produktu, który może zostać znacząco zmodyfikowany przed jego komercyjnym wydaniem. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

Ochrona sieci w usłudze Microsoft Defender dla punktu końcowego jest domyślnie włączona. Administratorzy mogą wykonać poniższe kroki, aby skonfigurować obsługę zarządzania aplikacjami mobilnymi na potrzeby ochrony sieci na urządzeniach iOS.

1. W Microsoft Endpoint Manager Administracja przejdź do pozycji Aplikacje > Zasady konfiguracji aplikacji. Utwórz nowe zasady konfiguracji aplikacji.
   :::image type="content" source="images/addiosconfig.png" alt-text="Dodaj zasady konfiguracji." lightbox="images/addiosconfig.png":::
   
2. Podaj nazwę i opis, aby jednoznacznie zidentyfikować zasady. Następnie kliknij pozycję "Wybierz aplikacje publiczne" i wybierz pozycję "Microsoft Defender" dla pozycji Platforma iOS/IPadOS :::image type="content" source="images/nameiosconfig.png" alt-text="Nadaj konfiguracji nazwę." lightbox="images/nameiosconfig.png":::
   
3. Na stronie Ustawienia dodaj wartość "DefenderNetworkProtectionEnable" jako klucz i wartość "false", aby wyłączyć ochronę sieci. (Ochrona sieci jest domyślnie włączona) :::image type="content" source="images/addiosconfigvalue.png" alt-text="Dodaj wartość konfiguracji." lightbox="images/addiosconfigvalue.png":::
   
4. W przypadku innych konfiguracji związanych z ochroną sieci dodaj następujące klucze i odpowiednią odpowiednią wartość.

    |Klucz| Wartość domyślna (true-enable, false-disable)|Opis|
    |---|---|---|
    |DefenderEndUserTrustFlowEnable| False | Włączanie użytkownikom zaufania do sieci i certyfikatów|
    |DefenderNetworkProtectionAutoRemediation| True |To ustawienie jest używane przez administratora IT do włączania lub wyłączania alertów korygowania wysyłanych, gdy użytkownik wykonuje działania korygujące, takie jak przełączanie się do bezpieczniejszych punktów dostępu w sieci WIFI lub usuwanie podejrzanych certyfikatów wykrytych przez usługę Defender|
    |DefenderNetworkProtectionPrivacy| True |To ustawienie jest zarządzane przez administratora IT w celu włączenia lub wyłączenia prywatności w ochronie sieci|
  
5. W sekcji Przypisania administrator może wybrać grupy użytkowników do uwzględnienia i wykluczenia z zasad.
   :::image type="content" source="images/assigniosconfig.png" alt-text="Przypisywanie konfiguracji." lightbox="images/assigniosconfig.png":::
   
6. Przejrzyj i utwórz zasady konfiguracji.

## <a name="co-existence-of-multiple-vpn-profiles"></a>Współistnienie wielu profilów sieci VPN

Usługa Apple iOS nie obsługuje wielu sieci VPN na całym urządzeniu, które mają być aktywne jednocześnie. Chociaż na urządzeniu może istnieć wiele profilów sieci VPN, tylko jedna sieć VPN może być aktywna jednocześnie.

## <a name="configure-microsoft-defender-for-endpoint-risk-signal-in-app-protection-policy-mam"></a>Konfigurowanie sygnału Ochrona punktu końcowego w usłudze Microsoft Defender ryzyka w zasadach ochrony aplikacji (MAM)

Ochrona punktu końcowego w usłudze Microsoft Defender można skonfigurować do wysyłania sygnałów zagrożeń do użycia w zasadach ochrony aplikacji (APP, znanej również jako MAM) w systemie iOS/iPadOS. Dzięki tej możliwości można również chronić dostęp do danych firmowych z niezarejestrowanych urządzeń za pomocą Ochrona punktu końcowego w usłudze Microsoft Defender.

Poniżej przedstawiono kroki konfigurowania zasad ochrony aplikacji za pomocą Ochrona punktu końcowego w usłudze Microsoft Defender:

1. Skonfiguruj połączenie z dzierżawy Microsoft Endpoint Manager, aby Ochrona punktu końcowego w usłudze Microsoft Defender. W [centrum administracyjnym programu Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) przejdź do pozycji **Łączniki i tokeny** **administracji** \> dzierżawy **Ochrona punktu końcowego w usłudze Microsoft Defender** (w obszarze Między platformami\>) lub **Zabezpieczenia punktu końcowego** \> **Ochrona punktu końcowego w usłudze Microsoft Defender** (w obszarze Konfiguracja) i włącz przełączniki w obszarze **Zasady ochrony aplikacji Ustawienia dla iOS**.

2. Wybierz Zapisz. Powinien zostać **wyświetlony stan połączenia** jest teraz ustawiony na **włączone**.

3. Tworzenie zasad ochrony aplikacji: po zakończeniu konfigurowania łącznika Ochrona punktu końcowego w usłudze Microsoft Defender przejdź do obszaru **Aplikacje** \> **Ochrona aplikacji zasad** (w obszarze Zasady), aby utworzyć nowe zasady lub zaktualizować istniejące.

4. Wybierz ustawienia platformy, **Aplikacje, Ochrona danych, Wymagania dotyczące dostępu** wymagane przez organizację dla zasad.

5. W obszarze **Warunkowe uruchamianie** \> **Urządzenia** znajdziesz ustawienie **Maksymalny dozwolony poziom zagrożenia urządzenia**. Należy to skonfigurować na wartość Niska, Średnia, Wysoka lub Zabezpieczona. Dostępne akcje to **Blokuj dostęp** lub **Wyczyść dane**. Może zostać wyświetlone okno dialogowe informacyjne, aby upewnić się, że łącznik został skonfigurowany przed zastosowaniem tego ustawienia. Jeśli łącznik jest już skonfigurowany, możesz zignorować to okno dialogowe.

6. Zakończ z przypisaniami i zapisz zasady.

Aby uzyskać więcej informacji na temat zasad zarządzania aplikacjami mobilnymi lub ochrony aplikacji, zobacz [iOS ustawienia zasad ochrony aplikacji](/mem/intune/apps/app-protection-policy-settings-ios).

### <a name="deploying-microsoft-defender-for-endpoint-for-mam-or-on-unenrolled-devices"></a>Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender na potrzeby zarządzania aplikacjami mobilnymi lub na niezarejestrowanych urządzeniach

Ochrona punktu końcowego w usłudze Microsoft Defender na iOS włącza scenariusz zasad ochrony aplikacji i jest dostępna w sklepie apple app store. Użytkownicy końcowi powinni zainstalować najnowszą wersję aplikacji bezpośrednio ze sklepu Apple App Store.

## <a name="privacy-controls"></a>Mechanizmy kontroli prywatności

> [!IMPORTANT]
> Mechanizmy kontroli prywatności dla Ochrona punktu końcowego w usłudze Microsoft Defender w iOS są w wersji zapoznawczej. Poniższe informacje dotyczą wstępnie wydanego produktu, który może zostać znacząco zmodyfikowany przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

### <a name="configure-privacy-in-phish-alert-report"></a>Konfigurowanie prywatności w raporcie alertów języka phish

Klienci mogą teraz włączyć kontrolę prywatności dla raportu phish wysłanego przez Ochrona punktu końcowego w usłudze Microsoft Defender na iOS. Zapewni to, że nazwa domeny nie zostanie wysłana jako część alertu phish za każdym razem, gdy witryna internetowa języka phish zostanie wykryta i zablokowana przez Ochrona punktu końcowego w usłudze Microsoft Defender.

Wykonaj poniższe kroki, aby włączyć prywatność i nie zbierać nazwy domeny w ramach raportu alertów języka phish.

1. W [Microsoft Endpoint Manager centrum administracyjnym](https://go.microsoft.com/fwlink/?linkid=2109431) i przejdź do obszaru Zasady  > **konfiguracji aplikacji** **Aplikacje** > **Dodaj** > **zarządzane urządzenia**.

2. Nadaj zasadom nazwę **Platform > iOS/iPadOS**, wybierz typ profilu.

3. Wybierz **Ochrona punktu końcowego w usłudze Microsoft Defender** jako aplikację docelową.

4. Na stronie Ustawienia wybierz pozycję **Użyj projektanta konfiguracji** i dodaj **kolumnę DefenderExcludeURLInReport** jako klucz i typ wartości jako wartość **logiczną**.

   - Aby włączyć prywatność i nie zbierać nazwy domeny, wprowadź wartość jako `true` i przypisz te zasady użytkownikom. Domyślnie ta wartość jest ustawiona na `false`.

   - W przypadku użytkowników z kluczem ustawionym jako `true`alert phish nie będzie zawierać informacji o nazwie domeny za każdym razem, gdy złośliwa witryna zostanie wykryta i zablokowana przez usługę Defender for Endpoint.

5. Kliknij przycisk **Dalej** i przypisz ten profil do urządzeń/użytkowników docelowych.

Włączenie lub wyłączenie powyższych mechanizmów kontroli prywatności nie wpłynie na sprawdzanie zgodności urządzeń ani dostęp warunkowy.

## <a name="configure-compliance-policy-against-jailbroken-devices"></a>Konfigurowanie zasad zgodności na urządzeniach ze zdjętymi zabezpieczeniami systemu

Aby chronić dane firmowe przed dostępem na urządzeniach ze zdjętymi zabezpieczeniami systemu iOS, zalecamy skonfigurowanie następujących zasad zgodności na Intune.

> [!NOTE]
> Wykrywanie jailbreak jest funkcją zapewnianą przez Ochrona punktu końcowego w usłudze Microsoft Defender na iOS. Zalecamy jednak skonfigurowanie tych zasad jako dodatkowej warstwy ochrony przed scenariuszami jailbreak.

Wykonaj poniższe kroki, aby utworzyć zasady zgodności dla urządzeń ze zdjętymi zabezpieczeniami systemu.

1. W [centrum administracyjnym Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) przejdź do obszaru **Zasady zgodności** **urządzeń** -> **Utwórz zasady** -> . Wybierz pozycję "iOS/iPadOS" jako platformę i kliknij pozycję **Utwórz**.

   :::image type="content" source="images/ios-jb-policy.png" alt-text="Karta Tworzenie zasad" lightbox="images/ios-jb-policy.png":::

1. Określ nazwę zasad, na przykład "Zasady zgodności dla jailbreaku".

1. Na stronie ustawienia zgodności kliknij, aby rozwinąć sekcję **Kondycja urządzenia** i kliknij pozycję **Blokuj** dla **urządzeń ze zdjętymi zabezpieczeniami systemu** .

   :::image type="content" source="images/ios-jb-settings.png" alt-text="Karta Ustawienia zgodności" lightbox="images/ios-jb-settings.png":::

1. W sekcji **Akcje dotyczące niezgodności** wybierz akcje zgodnie z wymaganiami i wybierz pozycję **Dalej**.

   :::image type="content" source="images/ios-jb-actions.png" alt-text="Karta Akcje dotyczące niezgodności" lightbox="images/ios-jb-actions.png":::

1. W sekcji **Przypisania** wybierz grupy użytkowników, które chcesz uwzględnić dla tych zasad, a następnie wybierz pozycję **Dalej**.

1. W sekcji **Przeglądanie i tworzenie** sprawdź, czy wszystkie wprowadzone informacje są poprawne, a następnie wybierz pozycję **Utwórz**.

## <a name="configure-custom-indicators"></a>Konfigurowanie niestandardowych wskaźników

Usługa Defender for Endpoint w iOS umożliwia administratorom konfigurowanie niestandardowych wskaźników również na urządzeniach iOS. Aby uzyskać więcej informacji na temat konfigurowania wskaźników niestandardowych, zobacz [Zarządzanie wskaźnikami](/microsoft-365/security/defender-endpoint/manage-indicators).

> [!NOTE]
> Usługa Defender for Endpoint na iOS obsługuje tworzenie niestandardowych wskaźników tylko dla adresów IP i adresów URL/domen.

## <a name="configure-option-to-send-in-app-feedback"></a>Konfigurowanie opcji wysyłania opinii w aplikacji 

Klienci mają teraz możliwość skonfigurowania możliwości wysyłania danych opinii do firmy Microsoft w aplikacji Defender for Endpoint. Dane opinii pomagają firmie Microsoft ulepszać produkty i rozwiązywać problemy.

> [!NOTE]
> W przypadku klientów korzystających z chmury dla instytucji rządowych USA zbieranie danych opinii jest domyślnie **wyłączone** . 

Wykonaj następujące kroki, aby skonfigurować opcję wysyłania danych opinii do firmy Microsoft:

1. W [Microsoft Endpoint Manager centrum administracyjnym](https://go.microsoft.com/fwlink/?linkid=2109431) i przejdź do obszaru Zasady  > **konfiguracji aplikacji** **Aplikacje** > **Dodaj** > **zarządzane urządzenia**.

1. Nadaj zasadom nazwę **Platform > iOS/iPadOS**, wybierz typ profilu.

1. Wybierz **Ochrona punktu końcowego w usłudze Microsoft Defender** jako aplikację docelową.

1. Na stronie Ustawienia wybierz pozycję **Użyj projektanta konfiguracji** i dodaj wartość **DefenderSendFeedback** jako klucz i typ wartości jako **wartość logiczną**.
   
   - Aby usunąć możliwość przekazywania opinii przez użytkowników końcowych, ustaw wartość jako `false` i przypisz te zasady do użytkowników. Domyślnie ta wartość jest ustawiona na `true`. W przypadku klientów rządowych USA wartość domyślna jest ustawiona na wartość "false".
   
   - W przypadku użytkowników z kluczem ustawionym jako `true`, w aplikacji będzie dostępna opcja wysyłania danych opinii do firmy Microsoft (menu > Pomoc & opinie > wysyłanie opinii do firmy Microsoft)

1. Kliknij przycisk **Dalej** i przypisz ten profil do urządzeń/użytkowników docelowych.

## <a name="report-unsafe-site"></a>Zgłaszanie niebezpiecznej witryny

Witryny wyłudzające informacje podszywają się pod zaufane strony internetowe w celu uzyskania informacji osobistych lub finansowych. Odwiedź stronę [Przekaż opinię na temat ochrony sieci](https://www.microsoft.com/wdsi/filesubmission/exploitguard/networkprotection) , jeśli chcesz zgłosić witrynę internetową, która może być witryną wyłudzającą informacje.
