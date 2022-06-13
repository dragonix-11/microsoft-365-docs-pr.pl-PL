---
title: Rozwiązywanie problemów i znajdowanie odpowiedzi na często zadawane pytania dotyczące Ochrona punktu końcowego w usłudze Microsoft Defender na iOS
description: Rozwiązywanie problemów i często zadawane pytania — Ochrona punktu końcowego w usłudze Microsoft Defender na iOS
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, ios, troubleshoot, faq, how to
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
ms.openlocfilehash: ae6e65d99a82bdf4a9c0adbb740c6e5b969f4b68
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66016333"
---
# <a name="troubleshoot-issues-and-find-answers-to-faqs-on-microsoft-defender-for-endpoint-on-ios"></a>Rozwiązywanie problemów i znajdowanie odpowiedzi na często zadawane pytania dotyczące Ochrona punktu końcowego w usłudze Microsoft Defender na iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Ten temat zawiera informacje dotyczące rozwiązywania problemów, które ułatwiają rozwiązywanie problemów, które mogą wystąpić podczas korzystania z Ochrona punktu końcowego w usłudze Microsoft Defender na iOS.

> [!NOTE]
> Usługa Defender for Endpoint w iOS będzie używać sieci VPN w celu zapewnienia funkcji ochrony sieci Web. Nie jest to zwykła sieć VPN i jest lokalną/samopętlaną siecią VPN, która nie przyjmuje ruchu poza urządzeniem.

## <a name="apps-dont-work-when-vpn-is-turned-on"></a>Aplikacje nie działają po włączeniu sieci VPN
Niektóre aplikacje przestają działać po wykryciu aktywnej sieci VPN. Sieć VPN można wyłączyć podczas korzystania z takich aplikacji.

Domyślnie usługa Defender for Endpoint na iOS obejmuje i włącza funkcję ochrony w Internecie. [Ochrona w Internecie](web-protection-overview.md) pomaga zabezpieczyć urządzenia przed zagrożeniami internetowymi i chronić użytkowników przed atakami wyłudzania informacji. Usługa Defender for Endpoint w iOS używa sieci VPN w celu zapewnienia tej ochrony. Należy pamiętać, że jest to lokalna sieć VPN, w przeciwieństwie do tradycyjnej sieci VPN, ruch sieciowy nie jest wysyłany poza urządzenie.

Mimo że jest domyślnie włączona, mogą wystąpić pewne przypadki, które wymagają wyłączenia sieci VPN. Na przykład chcesz uruchomić niektóre aplikacje, które nie działają po skonfigurowaniu sieci VPN. W takich przypadkach można wyłączyć sieć VPN bezpośrednio z aplikacji Defender for Endpoint lub wykonać następujące kroki:

1. Na urządzeniu iOS otwórz aplikację **Ustawienia**, kliknij lub naciśnij pozycję **Ogólne**, a następnie sieć **VPN**.
1. Kliknij lub naciśnij przycisk "i" dla Ochrona punktu końcowego w usłudze Microsoft Defender.
1. Wyłącz **Połączenie na żądanie**, aby wyłączyć sieć VPN.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-vpn-config.png" alt-text="Opcja Połączenie na żądanie" lightbox="images/ios-vpn-config.png":::

> [!NOTE]
> Usługa Web Protection nie będzie dostępna po wyłączeniu sieci VPN. Aby ponownie włączyć usługę Web Protection, otwórz aplikację Ochrona punktu końcowego w usłudze Microsoft Defender na urządzeniu i włącz usługę Web Protection.

## <a name="coexistence-with-multiple-vpn-profiles"></a>Współistnienie z wieloma profilami sieci VPN

Firma Apple iOS nie obsługuje wielu sieci VPN **na całym urządzeniu**, które mają być aktywne jednocześnie. Chociaż na urządzeniu może istnieć wiele profilów sieci VPN, tylko jedna sieć VPN może być aktywna jednocześnie. Jeśli chcesz użyć innej sieci VPN na urządzeniu, możesz wyłączyć usługę Defender for Endpoint VPN podczas korzystania z drugiej sieci VPN.

## <a name="battery-consumption"></a>Zużycie baterii

Aby zapewnić ochronę przez cały czas przed zagrożeniami internetowymi, Ochrona punktu końcowego w usłudze Microsoft Defender musi działać w tle przez cały czas. Może to prowadzić do niewielkiego wzrostu ogólnego zużycia baterii urządzenia. Jeśli widzisz znaczne zużycie baterii, [prześlij nam opinię](ios-troubleshoot.md#send-in-app-feedback) , a my zbadamy sprawę.

Ponadto w aplikacji Ustawienia iOS pokazuje tylko użycie baterii aplikacji, które są widoczne dla użytkownika przez określony czas. Użycie baterii przez aplikacje wyświetlane na ekranie jest tylko przez ten czas i jest obliczane przez iOS na podstawie wielu czynników, w tym użycia procesora CPU i sieci. Ochrona punktu końcowego w usłudze Microsoft Defender używa lokalnej/sprzężonej sieci VPN w tle do sprawdzania ruchu internetowego pod kątem złośliwych witryn sieci Web lub połączeń. Pakiety sieciowe z dowolnej aplikacji przechodzą przez tę kontrolę, co powoduje niedokładne obliczenie użycia baterii Ochrona punktu końcowego w usłudze Microsoft Defender. Rzeczywiste zużycie baterii Ochrona punktu końcowego w usłudze Microsoft Defender jest mniejsze niż to, co jest wyświetlane na stronie Ustawienia baterii na urządzeniu.

Należy pamiętać, że używana sieć VPN jest lokalną siecią VPN i w przeciwieństwie do tradycyjnej sieci VPN ruch sieciowy nie jest wysyłany poza urządzenie.

## <a name="data-usage"></a>Użycie danych

Ochrona punktu końcowego w usłudze Microsoft Defender używa lokalnej/sprzężonej sieci VPN do sprawdzania ruchu internetowego pod kątem złośliwych witryn internetowych lub połączeń. Z tego powodu Ochrona punktu końcowego w usłudze Microsoft Defender użycie danych może być niedokładnie rozliczane. Zaobserwowaliśmy również, że jeśli urządzenie jest tylko w sieci komórkowej, użycie danych zgłoszone przez dostawcę usług jest bardzo zbliżone do rzeczywistego zużycia, podczas gdy w aplikacji Ustawienia liczby mogą być niedokładne.

Podobne obserwacje mamy również w przypadku innych usług sieci VPN.

Ponadto ważne jest, aby Ochrona punktu końcowego w usłudze Microsoft Defender była aktualna z naszymi usługami zaplecza w celu zapewnienia lepszej ochrony.

## <a name="report-unsafe-site"></a>Zgłaszanie niebezpiecznej witryny

Witryny wyłudzające informacje podszywają się pod zaufane witryny internetowe w celu uzyskania informacji osobistych lub finansowych. Odwiedź stronę [Przekaż opinię na temat ochrony sieci](https://www.microsoft.com/wdsi/support/report-unsafe-site) , aby zgłosić witrynę internetową, która może być witryną wyłudzającą informacje.

## <a name="malicious-site-detected"></a>Wykryto złośliwą witrynę

Ochrona punktu końcowego w usłudze Microsoft Defender chroni przed wyłudzaniem informacji lub innymi atakami internetowymi. Jeśli zostanie wykryta złośliwa witryna, połączenie zostanie zablokowane, a alert zostanie wysłany do portalu Microsoft 365 Defender organizacji. Alert zawiera nazwę domeny połączenia, zdalny adres IP i szczegóły urządzenia.

Ponadto powiadomienie jest wyświetlane na urządzeniu iOS. Naciśnięcie powiadomienia powoduje otwarcie następującego ekranu, aby użytkownik przejrzał szczegóły.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/ios-phish-alert.png" alt-text="Witryna zgłoszona jako niebezpieczne powiadomienie" lightbox="images/ios-phish-alert.png":::

## <a name="device-not-seen-on-the-defender-for-endpoint-console-after-onboarding"></a>Urządzenie nie jest widoczne w konsoli usługi Defender for Endpoint po dołączeniu

Po dołączeniu urządzenie może zostać wyświetlone w spisie urządzeń w konsoli zabezpieczeń usługi Defender for Endpoint. Upewnij się również, że urządzenie jest poprawnie zarejestrowane w Azure Active Directory, a urządzenie ma łączność z Internetem. W celu pomyślnego dołączenia urządzenie musi zostać zarejestrowane za pośrednictwem Microsoft Authenticator lub Intune — Portal firmy, a użytkownik musi zalogować się przy użyciu tego samego konta, za pomocą którego urządzenie jest zarejestrowane w Azure AD.

> [!NOTE]
> Czasami nazwa urządzenia nie jest zgodna z nazwą w konsoli Microsoft Endpoint Manager (Intune). Nazwa urządzenia w konsoli usługi Defender for Endpoint ma format> modelu <username_iPhone/iPad. Możesz również użyć Azure AD identyfikatora urządzenia, aby zidentyfikować urządzenie w konsoli usługi Defender for Endpoint.

## <a name="data-and-privacy"></a>Dane i prywatność

Aby uzyskać szczegółowe informacje o zbieranych danych i ochronie prywatności, zobacz [Informacje o ochronie prywatności — Ochrona punktu końcowego w usłudze Microsoft Defender na iOS](ios-privacy.md).

## <a name="connectivity-issue-on-cellular-network"></a>Problem z łącznością w sieci komórkowej

Jeśli masz problemy z łącznością z Internetem w sieci komórkowej, sprawdź, czy Ochrona punktu końcowego w usłudze Microsoft Defender ma włączone dane komórkowe: Otwórz aplikację Ustawienia > ms defender > upewnij się, że dla usługi MS Defender włączono "dane komórkowe".

Jeśli nadal występują problemy z łącznością, sprawdź, czy włączenie/wyłączenie trybu samolotowego pomaga rozwiązać ten problem. Jeśli problem będzie się powtarzać, [wyślij do nas dzienniki](ios-troubleshoot.md#send-in-app-feedback).

## <a name="issues-on-supervised-devices-with-content-filter-profile-installed"></a>Problemy na urządzeniach nadzorowanych z zainstalowanym profilem filtru zawartości

Wystąpił problem na urządzeniach nadzorowanych z zainstalowanym filtrem zawartości usługi Defender for Endpoint. Jeśli zauważysz spowolnienie lub opóźnienie łączności internetowej na takich urządzeniach, odinstaluj lub usuń profil filtru zawartości z urządzenia. Pracujemy nad rozwiązaniem tego problemu i zaktualizujemy to miejsce po rozwiązaniu problemu. 

## <a name="issues-during-app-updates-from-the-app-store"></a>Problemy podczas aktualizacji aplikacji ze sklepu z aplikacjami

Jeśli zauważysz problemy podczas aktualizowania aplikacji za pośrednictwem sklepu z aplikacjami (automatyczne aktualizacje lub aktualizacje ręczne), może być konieczne ponowne uruchomienie urządzenia. Jeśli to nie rozwiąże problemu, możesz wyłączyć sieć VPN usługi Defender i wykonać aktualizację aplikacji. Możesz również przekazać opinię w aplikacji, aby zgłosić ten problem.

## <a name="send-in-app-feedback"></a>Wysyłanie opinii w aplikacji

Jeśli użytkownik napotka problem, który nie został jeszcze rozwiązany w powyższych sekcjach lub nie może rozwiązać problemu przy użyciu wymienionych kroków, użytkownik może przekazać opinię w aplikacji wraz z danymi diagnostycznymi. Następnie nasz zespół zbada dzienniki, aby zapewnić odpowiednie rozwiązanie. Użytkownicy mogą użyć następujących kroków, aby wysłać opinię:

- Otwórz aplikację MSDefender na urządzeniu z systemem iOS/iPadOS.
- Naciśnij pozycję Menu (ikona profilu) w lewym górnym rogu.
- Naciśnij **pozycję Wyślij opinię**.
- Wybierz jedną z podanych opcji. Aby zgłosić problem, wybierz **pozycję Nie podoba mi się coś**.
- Podaj szczegóły problemu, z którym się borykasz, i zaznacz opcję **Wyślij dane diagnostyczne**. Zalecamy uwzględnienie adresu e-mail, aby zespół mógł skontaktować się z Tobą w celu uzyskania rozwiązania lub dalszych czynności.
- Naciśnij pozycję **Prześlij** , aby pomyślnie wysłać opinię.
