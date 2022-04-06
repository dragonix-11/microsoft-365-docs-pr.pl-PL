---
title: Rozwiązywanie problemów i znajdowanie odpowiedzi na często zadawane pytania dotyczące aplikacji Ochrona punktu końcowego w usłudze Microsoft Defender systemie iOS
description: Rozwiązywanie problemów i często zadawane pytania — informacje Ochrona punktu końcowego w usłudze Microsoft Defender w systemie iOS
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, ios, rozwiązywanie problemów, często zadawane pytania,  how to
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
ms.openlocfilehash: bc8cda3fb61ec9338b95eed58f5f0a70e1deb3e1
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469366"
---
# <a name="troubleshoot-issues-and-find-answers-to-faqs-on-microsoft-defender-for-endpoint-on-ios"></a>Rozwiązywanie problemów i znajdowanie odpowiedzi na często zadawane pytania dotyczące aplikacji Ochrona punktu końcowego w usłudze Microsoft Defender systemie iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Ten temat zawiera informacje dotyczące rozwiązywania problemów, które mogą się pojawić podczas korzystania Ochrona punktu końcowego w usłudze Microsoft Defender systemie iOS.



> [!NOTE]
> Usługa Defender for Endpoint w systemie iOS korzysta z połączenia VPN w celu zapewnienia funkcji ochrony sieci Web. Nie jest to zwykły sieci VPN i jest to lokalny/samopętny vpn, który nie przejmuje ruchu poza urządzenie.

## <a name="apps-dont-work-when-vpn-is-turned-on"></a>Aplikacje nie działają, gdy jest włączona sieć VPN
Niektóre aplikacje przestają działać po wykryciu aktywnego połączenia VPN. W czasie korzystania z takich aplikacji możesz wyłączyć sieć VPN. 

Domyślnie program Defender for Endpoint w systemie iOS zawiera i włącza funkcję ochrony sieci Web. [Ochrona sieci Web](web-protection-overview.md) pomaga zabezpieczyć urządzenia przed zagrożeniami internetowymi i chronić użytkowników przed atakami wyłudzających informacje. W celu zapewnienia tej ochrony usługa Defender for Endpoint w systemie iOS używa połączenia VPN. Zwróć uwagę, że jest to lokalny interfejs VPN i w przeciwieństwie do tradycyjnych sieci VPN ruch sieciowy nie jest wysyłany poza urządzenie.

Gdy ta funkcja jest domyślnie włączona, może być konieczne wyłączenie połączenia VPN w niektórych przypadkach. Na przykład chcesz uruchomić niektóre aplikacje, które nie działają po skonfigurowaniu połączenia VPN. W takich przypadkach możesz wyłączyć sieć VPN bezpośrednio z aplikacji Defender for Endpoint lub wykonać następujące czynności:

1. Na urządzeniu z systemem iOS otwórz aplikację sieci **Ustawienia**, kliknij lub naciśnij pozycję **Ogólne**, a następnie pozycję **VPN**.
1. Kliknij lub naciśnij przycisk "i", aby Ochrona punktu końcowego w usłudze Microsoft Defender.
1. Aby wyłączyć sieć **VPN Połączenie na** żądanie.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-vpn-config.png" alt-text="Opcja Połączenie na żądanie" lightbox="images/ios-vpn-config.png":::

> [!NOTE]
> Ochrona sieci Web nie będzie dostępna po wyłączeniu połączenia VPN. Aby ponownie włączyć ochronę sieci Web, otwórz aplikację Ochrona punktu końcowego w usłudze Microsoft Defender na urządzeniu i włącz ochronę sieci Web.

## <a name="coexistence-with-multiple-vpn-profiles"></a>Współistnienie z wieloma profilami VPN

System Apple iOS nie **obsługuje jednoczesnego** działania wielu sieci VPN dla całego urządzenia. Na urządzeniu może istnieć wiele profilów VPN, ale tylko jeden z nich może być aktywny jednocześnie. Jeśli chcesz korzystać z innego połączenia VPN na urządzeniu, możesz wyłączyć usługę Defender for Endpoint VPN podczas korzystania z innego połączenia VPN.

## <a name="battery-consumption"></a>Zużycie baterii

Aby zapewnić ochronę przez cały czas przed zagrożeniami internetowymi, Ochrona punktu końcowego w usłudze Microsoft Defender musi przez cały czas działać w tle. Może to powodować niewielkie zwiększenie ogólnego zużycia baterii w Twoim urządzeniu. W przypadku znacznej wymiany baterii prześlij nam opinię[](ios-troubleshoot.md#send-in-app-feedback), a my przejdę do badania.

Ponadto w aplikacji Ustawienia system iOS pokazuje zużycie baterii tylko w przypadku aplikacji widocznych dla użytkownika przez określony czas. Zużycie baterii przez aplikacje wyświetlane na ekranie dotyczy tylko tego czasu i jest obliczane przez system iOS na podstawie różnych czynników, takich jak procesor i użycie sieci. Ochrona punktu końcowego w usłudze Microsoft Defender sieci VPN w tle używa sieci vpn w pętli lokalnej w celu sprawdzenia ruchu w sieci Web pod każdym złośliwymi witrynami sieci Web lub połączeniami. Pakiety sieciowe z dowolnej aplikacji przejść przez ten proces sprawdzania, co powoduje, że zużycie baterii Ochrona punktu końcowego w usłudze Microsoft Defender zostać obliczone nieprawidłowo. Rzeczywiste zużycie baterii w Ochrona punktu końcowego w usłudze Microsoft Defender jest mniejsze niż to, co jest widoczne na stronie baterii Ustawienia na urządzeniu.

Pamiętaj, że używany interfejs VPN to lokalny vpn, a w przeciwieństwie do tradycyjnego połączenia VPN ruch sieciowy nie jest wysyłany poza urządzenie.

## <a name="data-usage"></a>Zużycie danych

Ochrona punktu końcowego w usłudze Microsoft Defender sieci VPN w celu sprawdzenia ruchu sieci Web pod czyjąś złośliwą witryną internetową lub połączeniami używa sieci VPN w sieci lokalnej. Z tego powodu użycie Ochrona punktu końcowego w usłudze Microsoft Defender danych może być niedokładnie uwzględnione. Zauważyliśmy również, że jeśli urządzenie działa tylko w sieci komórkowej, użycie danych zgłoszonych przez usługę usługodawca jest bardzo zbliżone do rzeczywistego zużycia, natomiast w aplikacji Ustawienia firma Apple pokazuje od 1,5 do 2x rzeczywistych zużywanych danych.

Mamy podobne spostrzeżenia również w przypadku innych usług VPN i zgłaszaliśmy to do firmy Apple.

Ponadto bardzo ważne jest, Ochrona punktu końcowego w usłudze Microsoft Defender na bieżąco z naszymi usługami zaplecza, aby zapewnić lepszą ochronę.

## <a name="report-unsafe-site"></a>Zgłoś niebezpieczną witrynę

Witryny internetowe wyłudzujące informacje spersonifikują zaufane witryny internetowe w celu uzyskania informacji osobistych lub finansowych. Odwiedź stronę [Podaj opinię na temat ochrony sieci](https://www.microsoft.com/wdsi/support/report-unsafe-site) , aby zgłosić witrynę internetową, która może być witryną wyłudzającą informacje.

## <a name="malicious-site-detected"></a>Wykryto złośliwą witrynę

Ochrona punktu końcowego w usłudze Microsoft Defender zapewnia ochronę przed wyłudzaniem informacji i innymi atakami internetowymi. W przypadku wykrycia złośliwej witryny połączenie zostanie zablokowane i do portalu sieci Microsoft 365 Defender organizacji zostanie wysłany alert. Alert zawiera nazwę domeny połączenia, zdalny adres IP i szczegóły urządzenia.

Ponadto powiadomienie jest wyświetlane na urządzeniu z systemem iOS. Naciśnięcie powiadomienia spowoduje otwarcie następującego ekranu, na który użytkownik może przejrzeć szczegóły.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/ios-phish-alert.png" alt-text="Witryna zgłoszona jako niebezpieczna" lightbox="images/ios-phish-alert.png":::

## <a name="device-not-seen-on-the-defender-for-endpoint-console-after-onboarding"></a>Urządzenie nie jest widoczne w programie Defender dla konsoli końcowej po włoce.

Po dojechanie urządzenia do spisu urządzeń w konsoli zabezpieczeń Programu Defender for Endpoint może mi potrwać kilka godzin. Upewnij się też, że urządzenie zostało poprawnie zarejestrowane w u Azure Active Directory i ma łączność z Internetem. Aby można było pomyślnie wboardować urządzenie, musi zostać zarejestrowane za pośrednictwem programu Microsoft Authenticator lub Intune — Portal firmy i użytkownik musi zalogować się przy użyciu tego samego konta, na którym jest zarejestrowane urządzenie w usłudze Azure AD.

> [!NOTE]
> Czasami nazwa urządzenia jest z nim spójna w Microsoft Endpoint Manager (Intune). Nazwa urządzenia w programie Defender dla konsoli końcowej ma format <username_iPhone/iPad i>. Za pomocą identyfikatora urządzenia usługi Azure AD możesz także zidentyfikować urządzenie w programie Defender for Endpoint console.

## <a name="data-and-privacy"></a>Dane i prywatność

Aby uzyskać szczegółowe informacje na temat zbieranych danych i prywatności, zobacz [Informacje o prywatności — informacje Ochrona punktu końcowego w usłudze Microsoft Defender w systemie iOS](ios-privacy.md).

## <a name="connectivity-issue-on-cellular-network"></a>Problem z łącznością w sieci komórkowej

Jeśli masz problemy z łącznością z Internetem w sieci komórkowej, sprawdź, czy usługa Ochrona punktu końcowego w usłudze Microsoft Defender ma włączoną obsługę danych komórkowych: Otwórz aplikację Ustawienia app > MS Defender > upewnij się, że dla programu MS Defender włączono obsługę danych komórkowych.

Jeśli nadal masz problemy z łącznością, sprawdź, czy włączenie/wyłączenie trybu samolotowego pomaga rozwiązać ten problem. Jeśli problem będzie nadal występował, [wyślij nam dzienniki](ios-troubleshoot.md#send-in-app-feedback).

## <a name="issues-on-supervised-devices-with-content-filter-profile-installed"></a>Problemy na urządzeniach nadzorowanych z zainstalowanym profilem filtru zawartości

Występuje problem na urządzeniach nadzorowanych z zainstalowanym filtrem zawartości programu Defender for Endpoint. Jeśli obserwujesz opóźnienie lub opóźnienie łączności internetowej na takich urządzeniach, odinstaluj lub usuń profil filtru zawartości z urządzenia. Pracujemy nad rozwiązaniem tego problemu i zaktualizujemy to miejsce, gdy będziemy mieć rozwiązanie. 

## <a name="issues-during-app-updates-from-the-app-store"></a>Problemy podczas aktualizacji aplikacji ze sklepu z aplikacjami

Jeśli obserwujesz problemy, gdy aplikacja jest aktualizowana za pośrednictwem sklepu z aplikacjami (automatyczne lub ręczne aktualizacje), może być konieczne ponowne uruchomienie urządzenia. Jeśli to nie rozwiąże problemu, możesz wyłączyć sieć VPN programu Defender i przeprowadzić aktualizację aplikacji. Możesz również przekazać opinię w aplikacji, aby zgłosić ten problem.

## <a name="send-in-app-feedback"></a>Wysyłanie opinii w aplikacji

Jeśli użytkownik napotyka problem, który nie został jeszcze rozwiązany w powyższych sekcjach lub nie może rozwiązać problemu przy użyciu wymienionych czynności, może przekazać opinię w aplikacji wraz z danymi diagnostycznmi. Nasz zespół przeszuka dzienniki w celu podania odpowiedniego rozwiązania. Użytkownicy mogą przesyłać opinie, wykonać następujące czynności:

  - Otwórz aplikację MSDefender na urządzeniu z systemem iOS/iPadOS.
  - Naciśnij pozycję Menu (ikona profilu) w lewym górnym rogu.
  - Naciśnij **pozycję Wyślij opinię**.
  - Wybierz jedną z dostępnych opcji. Aby zgłosić problem, wybierz **pozycję Coś mi się nie podoba**.
  - Podaj szczegóły problemu, z którym masz do czynienia, i zaznacz pole **wyboru Wyślij dane diagnostyczne**. Zalecamy, aby dołączyć swój adres e-mail, aby zespół skontaktował się z Tobą w celu rozwiązania lub rozwiązania problemu.
  - Naciśnij **pozycję Prześlij** , aby pomyślnie wysłać opinię.
