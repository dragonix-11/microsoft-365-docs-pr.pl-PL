---
title: Zalecane zasady dotyczące bezpiecznej poczty e-mail — Microsoft 365 dla | przedsiębiorstwa Microsoft Docs
description: W tym artykule opisano zasady dotyczące zaleceń firmy Microsoft dotyczących sposobu stosowania zasad i konfiguracji poczty e-mail.
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
ms.openlocfilehash: 592b5733844dc6a3df1a1d207e3a2c3deda7d7b7
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66015219"
---
# <a name="policy-recommendations-for-securing-email"></a>Zalecenia dotyczące zasad dotyczące zabezpieczania poczty e-mail

W tym artykule opisano sposób implementowania zalecanych zasad Zero Trust tożsamości i dostępu do urządzeń w celu ochrony klientów poczty e-mail i poczty e-mail organizacji obsługujących nowoczesne uwierzytelnianie i dostęp warunkowy. Te wskazówki bazują na [zasadach wspólnej tożsamości i dostępu do urządzeń](identity-access-policies.md) , a także zawierają kilka dodatkowych zaleceń.

Te zalecenia są oparte na trzech różnych warstwach zabezpieczeń i ochrony, które mogą być stosowane w oparciu o stopień szczegółowości twoich potrzeb: **punkt początkowy**, **przedsiębiorstwo** i **wyspecjalizowane zabezpieczenia**. Więcej informacji na temat tych warstw zabezpieczeń i zalecanych systemów operacyjnych klienta, do których odnoszą się te zalecenia, można znaleźć we [wstępie do zalecanych zasad zabezpieczeń i konfiguracji](microsoft-365-policies-configurations.md).

Te zalecenia wymagają od użytkowników korzystania z nowoczesnych klientów poczty e-mail, w tym Outlook dla iOS i Android na urządzeniach przenośnych. Outlook dla iOS i Android zapewniają obsługę najlepszych funkcji Office 365. Te aplikacje Outlook mobilne są również wyposażone w funkcje zabezpieczeń, które obsługują korzystanie z urządzeń przenośnych i współpracują z innymi funkcjami zabezpieczeń w chmurze firmy Microsoft. Aby uzyskać więcej informacji, zobacz [Outlook iOS i często zadawane pytania dotyczące Android](/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-faq).

## <a name="update-common-policies-to-include-email"></a>Aktualizowanie typowych zasad w celu uwzględnienia poczty e-mail

Aby chronić pocztę e-mail, na poniższym diagramie przedstawiono zasady, które należy zaktualizować na podstawie typowych zasad dostępu do tożsamości i urządzeń.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-mail.png" alt-text="Podsumowanie aktualizacji zasad dotyczących ochrony dostępu do usługi Microsoft Exchange" lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-mail.png":::

Zwróć uwagę na dodanie nowych zasad dla Exchange Online do blokowania klientów ActiveSync. Wymusza to korzystanie z Outlook mobilnych.

Jeśli podczas ich konfigurowania uwzględniono Exchange Online i Outlook w zakresie zasad, musisz tylko utworzyć nowe zasady, aby zablokować klientów usługi ActiveSync. Przejrzyj zasady wymienione w poniższej tabeli i wprowadź zalecane dodatki lub upewnij się, że zostały one już uwzględnione. Każda zasada łączy się ze skojarzonymi instrukcjami konfiguracji w temacie [Common identity and device access policies (Typowe zasady dostępu do tożsamości i urządzeń](identity-access-policies.md)).

|Poziom ochrony|Policies (zasady)|Więcej informacji|
|---|---|---|
|**Punkt początkowy**|[Wymagaj uwierzytelniania wieloskładnikowego, gdy ryzyko logowania jest *średnie* lub *wysokie*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Dołączanie Exchange Online do przypisywania aplikacji w chmurze|
||[Blokuj klientów, którzy nie obsługują nowoczesnego uwierzytelniania](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|Dołączanie Exchange Online do przypisywania aplikacji w chmurze|
||[Stosowanie zasad ochrony danych aplikacji](identity-access-policies.md#apply-app-data-protection-policies)|Upewnij się, Outlook znajduje się na liście aplikacji. Pamiętaj, aby zaktualizować zasady dla każdej platformy (iOS, Android, Windows)|
||[Wymagaj zatwierdzonych aplikacji i ochrony aplikacji](identity-access-policies.md#require-approved-apps-and-app-protection)|Uwzględnij Exchange Online na liście aplikacji w chmurze|
||[Blokuj klientów activesync](#block-activesync-clients)|Dodaj te nowe zasady|
|**Enterprise**|[Wymagaj uwierzytelniania wieloskładnikowego, gdy ryzyko logowania jest *niskie*, *średnie* lub *wysokie*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Dołączanie Exchange Online do przypisywania aplikacji w chmurze|
||[Wymagaj zgodnych komputerów *i* urządzeń przenośnych](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Uwzględnij Exchange Online na liście aplikacji w chmurze|
|**Wyspecjalizowane zabezpieczenia**|[*Zawsze* wymagaj uwierzytelniania wieloskładnikowego](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Dołączanie Exchange Online do przypisywania aplikacji w chmurze|

## <a name="block-activesync-clients"></a>Blokuj klientów activesync

Exchange ActiveSync może służyć do synchronizowania danych komunikatów i kalendarzy na komputerach stacjonarnych i urządzeniach przenośnych.

W przypadku urządzeń przenośnych nowoczesne klienty Exchange ActiveSync obsługujące uwierzytelnianie, które nie obsługują zasad ochrony aplikacji Intune (lub obsługiwanych klientów, które nie są zdefiniowane w zasadach ochrony aplikacji) i Exchange ActiveSync klientów korzystających z uwierzytelniania podstawowego są blokowane na podstawie zasad dostępu warunkowego utworzonych w [programie Wymagaj zatwierdzonych aplikacji i ochrony aplikacji](identity-access-policies.md#require-approved-apps-and-app-protection).

Aby zablokować Exchange ActiveSync przy użyciu uwierzytelniania podstawowego na innych urządzeniach, wykonaj kroki opisane w temacie [Blokuj Exchange ActiveSync na wszystkich urządzeniach](/azure/active-directory/conditional-access/howto-policy-approved-app-or-app-protection#block-exchange-activesync-on-all-devices), co uniemożliwia Exchange ActiveSync klientom korzystającym z uwierzytelniania podstawowego na urządzeniach innych niż przenośne nawiązywanie połączenia z Exchange Online.

Zasady uwierzytelniania umożliwiają również [wyłączenie uwierzytelniania podstawowego](/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online), co wymusza użycie nowoczesnego uwierzytelniania przez wszystkie żądania dostępu klientów.

## <a name="limit-access-to-exchange-online-from-outlook-on-the-web"></a>Ograniczanie dostępu do Exchange Online z Outlook w sieci Web

Możesz ograniczyć użytkownikom możliwość pobierania załączników z Outlook w sieci Web na urządzeniach niezarządzanych. Użytkownicy na tych urządzeniach mogą wyświetlać i edytować te pliki przy użyciu usługi Office Online bez przeciekania i przechowywania plików na urządzeniu. Możesz również zablokować użytkownikom możliwość wyświetlania załączników na urządzeniu niezarządzanym.

W tym celu należy wykonać następujące czynności:

1. [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).
2. Jeśli nie masz jeszcze zasad skrzynki pocztowej OWA, utwórz je za pomocą polecenia cmdlet [New-OwaMailboxPolicy](/powershell/module/exchange/new-owamailboxpolicy) .
3. Jeśli chcesz zezwolić na wyświetlanie załączników, ale nie chcesz pobierać, użyj tego polecenia:

   ```powershell
   Set-OwaMailboxPolicy -Identity Default -ConditionalAccessPolicy ReadOnly
   ```

4. Jeśli chcesz zablokować załączniki, użyj następującego polecenia:

   ```powershell
   Set-OwaMailboxPolicy -Identity Default -ConditionalAccessPolicy ReadOnlyPlusAttachmentsBlocked
   ```

5. W Azure Portal utwórz nowe zasady dostępu warunkowego z następującymi ustawieniami:

   **Przypisania** \> **Użytkownicy i grupy**: wybierz odpowiednich użytkowników i grupy do uwzględnienia i wykluczenia.

   **Przypisania** \> **Aplikacje lub akcje** \> w chmurze **Aplikacje w** \> chmurze **Obejmują** \> **Wybieranie aplikacji**: wybierz **pozycję Office 365 Exchange Online**

   **Mechanizmy kontroli** \> dostępu **Sesja**: wybierz pozycję **Użyj ograniczeń wymuszonych przez aplikację**

## <a name="require-that-ios-and-android-devices-must-use-outlook"></a>Wymagaj, aby urządzenia iOS i Android używały Outlook

Aby zapewnić użytkownikom urządzeń iOS i Android dostęp tylko do zawartości służbowej przy użyciu Outlook dla iOS i Android, potrzebne są zasady dostępu warunkowego przeznaczone dla tych potencjalnych użytkowników.

Aby skonfigurować te zasady, zobacz [Zarządzanie dostępem do współpracy obsługi komunikatów przy użyciu Outlook dla iOS i Android](/mem/intune/apps/app-configuration-policies-outlook#apply-conditional-access).

## <a name="set-up-message-encryption"></a>Konfigurowanie szyfrowania komunikatów

Dzięki usłudze Microsoft Purview Message Encryption, która korzysta z funkcji ochrony w usłudze Azure Information Protection, twoja organizacja może łatwo udostępniać chronioną pocztę e-mail wszystkim osobom na dowolnym urządzeniu. Użytkownicy mogą wysyłać i odbierać chronione wiadomości z innymi organizacjami Microsoft 365, a także z innymi klientami przy użyciu Outlook.com, Gmail i innych usług poczty e-mail.

Aby uzyskać więcej informacji, zobacz [Konfigurowanie nowych funkcji szyfrowania komunikatów Office 365](../../compliance/set-up-new-message-encryption-capabilities.md).

## <a name="next-steps"></a>Następne kroki

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="Zasady dotyczące Microsoft 365 aplikacji w chmurze" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::

Skonfiguruj zasady dostępu warunkowego dla:

- [Microsoft Teams](teams-access-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)
