---
title: Bezpieczne zasady zalecane dla poczty e-mail Microsoft 365 dla firm | Microsoft Docs
description: W tym artykule opisano zasady dotyczące rekomendacji firmy Microsoft dotyczących stosowania zasad i konfiguracji poczty e-mail.
ms.author: dansimp
author: dansimp
manager: Laurawi
ms.prod: m365-security
ms.topic: article
audience: Admin
f1.keywords:
- NOCSH
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- remotework
- m365solution-identitydevice
- m365solution-scenario
ms.technology: mdo
ms.openlocfilehash: b4b47b5cd5b7f345d21f2fa60deec736d931c62f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473436"
---
# <a name="policy-recommendations-for-securing-email"></a>Zalecenia dotyczące zasad dotyczące zabezpieczania poczty e-mail

W tym artykule opisano sposób wdrażania zalecanych zasad dostępu do usługi Zero Trust i dostępu do urządzeń w celu ochrony poczty e-mail i klientów poczty e-mail organizacji, które obsługują nowoczesne uwierzytelnianie i dostęp warunkowy. Te wskazówki są kompilacją wspólnych zasad dostępu do [urządzeń](identity-access-policies.md) i tożsamości, a także zawierają dodatkowe zalecenia.

Zalecenia te są oparte na trzech różnych warstwach zabezpieczeń i ochrony, które można stosować w zależności od stopnia szczegółowości Twoich **potrzeb: punktu** początkowego **,** przedsiębiorstwa i **wyspecjalizowanego zabezpieczeń**. Możesz dowiedzieć się więcej o tych warstwach zabezpieczeń i zalecanych systemach operacyjnych klientów, do których odwoływowały się te zalecenia we wprowadzeniu zalecanych zasad zabezpieczeń [i konfiguracji](microsoft-365-policies-configurations.md).

Te zalecenia wymagają, aby użytkownicy korzystali z nowoczesnych klientów poczty e-mail, w tym Outlook dla systemów iOS i Android na urządzeniach przenośnych. Outlook dla systemów iOS i Android zapewniają obsługę najlepszych funkcji aplikacji Office 365. Te aplikacje Outlook są również projektowane przy użyciu funkcji zabezpieczeń, które obsługują korzystanie z urządzeń przenośnych i współpracują z innymi możliwościami zabezpieczeń w chmurze firmy Microsoft. Aby uzyskać więcej informacji, zobacz Artykuł [Outlook dla systemów iOS i Android — często zadawane pytania](/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-faq).

## <a name="update-common-policies-to-include-email"></a>Aktualizowanie typowych zasad w celu uwzględniania poczty e-mail

Aby chronić pocztę e-mail, na poniższym diagramie pokazano zasady do zaktualizowania na stronie wspólnej zasad dostępu do urządzeń i tożsamości.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-mail.png" alt-text="Podsumowanie aktualizacji zasad w celu ochrony dostępu do usługi Microsoft Exchange" lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-mail.png":::

Zwróć uwagę na dodanie nowych zasad do blokowania Exchange Online ActiveSync. Wymusza to korzystanie z Outlook urządzenia przenośnego.

Jeśli podczas ich Exchange Online do Outlook uwzględniono zasady, wystarczy utworzyć nowe zasady w celu blokowania klientów programu ActiveSync. Przejrzyj zasady wymienione w poniższej tabeli i upewnij się, że zostały one już dołączone, i upewnij się, że zostały one już uwzględnione. Każda zasada zawiera linki do skojarzonych instrukcji konfiguracji podanych w [tece Wspólne zasady dostępu do urządzeń i tożsamości](identity-access-policies.md).

|Poziom ochrony|Policies (zasady)|Więcej informacji|
|---|---|---|
|**Punkt początkowy**|[Wymagaj uwierzytelniania wieloskładnikowego, gdy ryzyko logowania *jest średnie* lub *wysokie*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Uwzględnianie Exchange Online przy przypisywaniu aplikacji w chmurze|
||[Blokowanie klientów, którzy nie obsługują nowoczesnego uwierzytelniania](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|Uwzględnianie Exchange Online przy przypisywaniu aplikacji w chmurze|
||[Stosowanie zasad ochrony danych aplikacji](identity-access-policies.md#apply-app-data-protection-policies)|Upewnij się Outlook że znajduje się na liście aplikacji. Pamiętaj o zaktualizowaniu zasad dla każdej platformy (systemy iOS, Android, Windows)|
||[Wymaganie zatwierdzonych aplikacji i ochrony aplikacji](identity-access-policies.md#require-approved-apps-and-app-protection)|Uwzględnianie Exchange Online na liście aplikacji w chmurze|
||[Blokowanie klientów programu ActiveSync](#block-activesync-clients)|Dodaj te nowe zasady|
|**Enterprise**|[Wymagaj uwierzytelniania wieloskładnikowego, gdy ryzyko logowania *jest niskie, średnie* lub *wysokie*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Uwzględnianie Exchange Online przy przypisywaniu aplikacji w chmurze|
||[Wymaganie zgodności komputerów i *urządzeń* przenośnych](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Uwzględnianie Exchange Online na liście aplikacji w chmurze|
|**Wyspecjalizowane zabezpieczenia**|[*Zawsze wymagaj* uwierzytelniania wieloskładnikowego](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Uwzględnianie Exchange Online przy przypisywaniu aplikacji w chmurze|

## <a name="block-activesync-clients"></a>Blokowanie klientów programu ActiveSync

Exchange ActiveSync służy do synchronizowania wiadomości i danych kalendarza na komputerach i urządzeniach przenośnych.

W przypadku urządzeń przenośnych klienci programu Exchange ActiveSync z nowoczesnym uwierzytelnianiem nie obsługujący zasad ochrony aplikacji programu Intune (lub obsługiwani klienci, którzy nie są zdefiniowani w zasadach ochrony aplikacji) oraz [klienci programu Exchange ActiveSync, którzy używają uwierzytelniania podstawowego, są blokowani na podstawie zasad dostępu warunkowego utworzonych w Wymagaj zatwierdzonych aplikacji i ochrony aplikacji](identity-access-policies.md#require-approved-apps-and-app-protection).

Aby zablokować Exchange ActiveSync przy użyciu uwierzytelniania podstawowego na innych urządzeniach, wykonaj czynności opisane Exchange ActiveSync Blokowanie połączeń na wszystkich urządzeniach[, co](/azure/active-directory/conditional-access/howto-policy-approved-app-or-app-protection#block-exchange-activesync-on-all-devices) uniemożliwi łączenie się klientów usługi Exchange ActiveSync korzystających z uwierzytelniania podstawowego na urządzeniach innych niż urządzenia przenośne Exchange Online.

Za pomocą zasad uwierzytelniania można [również wyłączyć uwierzytelnianie](/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online) podstawowe, które wymusza na wszystkich żądaniach dostępu klienta korzystanie z nowoczesnego uwierzytelniania.

## <a name="limit-access-to-exchange-online-from-outlook-on-the-web"></a>Ograniczanie dostępu do Exchange Online z Outlook w sieci Web

Możesz ograniczyć użytkownikom możliwość pobierania załączników z aplikacji Outlook w sieci Web urządzeniach nieza zarządzania. Użytkownicy na tych urządzeniach mogą wyświetlać i edytować te pliki za pomocą usługi Office Online bez wycieków i przechowywania plików na urządzeniu. Możesz również zablokować użytkownikom wyświetlanie załączników na urządzeniu niezamanektowym.

W tym celu należy wykonać następujące czynności:

1. [Połączenie do sesji zdalnej Exchange Online PowerShell](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).
2. Jeśli nie masz jeszcze zasad skrzynki pocztowej aplikacji OWA, utwórz je przy użyciu polecenia cmdlet [New-OwaMailboxPolicy](/powershell/module/exchange/new-owamailboxpolicy) .
3. Jeśli chcesz zezwolić na wyświetlanie załączników, ale nie na pobieranie ich, użyj tego polecenia:

   ```powershell
   Set-OwaMailboxPolicy -Identity Default -ConditionalAccessPolicy ReadOnly
   ```

4. Jeśli chcesz zablokować załączniki, użyj tego polecenia:

   ```powershell
   Set-OwaMailboxPolicy -Identity Default -ConditionalAccessPolicy ReadOnlyPlusAttachmentsBlocked
   ```

5. W Azure Portal utwórz nowe zasady dostępu warunkowego z tymi ustawieniami:

    \> Zadania **Użytkownicy i grupy**: Wybierz odpowiednich użytkowników i grupy, które chcesz uwzględnić lub wykluczyć.

    \> Zadania **Aplikacje lub akcje w chmurze** \> **Aplikacje w chmurze** \> **Uwzględnij** \> **Wybierz aplikacje**: Wybierz **Office 365 Exchange Online**

   **Kontrolki programu Access** \> **Sesja**: Wybierz **pozycję Użyj ograniczeń wymuszonych przez aplikację**

## <a name="require-that-ios-and-android-devices-must-use-outlook"></a>Wymaganie, aby urządzenia z systemami iOS i Android Outlook

Aby zapewnić, że użytkownicy urządzeń z systemami iOS i Android mogą uzyskać dostęp tylko do zawartości służbowej lub szkolnej przy użyciu aplikacji Outlook dla systemów iOS i Android, potrzebne są zasady dostępu warunkowego, które będą działać u tych potencjalnych użytkowników.

Aby uzyskać informacje na temat konfigurowania tych zasad, zobacz Zarządzanie dostępem do współpracy za pomocą wiadomości [przy Outlook dla systemów iOS i Android](/mem/intune/apps/app-configuration-policies-outlook#apply-conditional-access).

## <a name="set-up-message-encryption"></a>Konfigurowanie szyfrowania wiadomości

Dzięki nowym funkcjom szyfrowania wiadomości Office 365 (OME), które wykorzystują funkcje ochrony w usłudze Azure Information Protection, Twoja organizacja może łatwo udostępniać chronioną pocztę e-mail wszystkim osobom na dowolnym urządzeniu. Użytkownicy mogą wysyłać i odbierać chronione wiadomości z Microsoft 365 organizacji, a także osób niebędących klientami, korzystając z Outlook.com, Gmail i innych usług poczty e-mail.

Aby uzyskać więcej informacji, [zobacz Konfigurowanie nowych funkcji Office 365 szyfrowania wiadomości](../../compliance/set-up-new-message-encryption-capabilities.md).

## <a name="next-steps"></a>Następne kroki

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="Zasady dotyczące aplikacji Microsoft 365 chmurze" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::

Skonfiguruj zasady dostępu warunkowego dla:

- [Microsoft Teams](teams-access-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)
