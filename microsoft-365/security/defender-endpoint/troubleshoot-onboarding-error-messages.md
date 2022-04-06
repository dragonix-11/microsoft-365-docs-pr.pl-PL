---
title: Rozwiązywanie problemów z dołączaniem i komunikatami o błędach
description: Rozwiązywanie problemów z dołączaniem i komunikatami o błędach podczas kończenie konfigurowania Ochrona punktu końcowego w usłudze Microsoft Defender.
keywords: rozwiązywanie problemów, rozwiązywanie problemów, Azure Active Directory, dołączanie, komunikat o błędzie, komunikaty o błędach, microsoft defender for endpoint
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: cfbd91743ed2e61809d9e2b6f0243b5c327bdae4
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467560"
---
# <a name="troubleshoot-subscription-and-portal-access-issues"></a>Rozwiązywanie problemów z dostępem do subskrypcji i portalu

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-troublshootonboarding-abovefoldlink)

Ta strona zawiera szczegółowe kroki rozwiązywania problemów, które mogą wystąpić podczas konfigurowania Ochrona punktu końcowego w usłudze Microsoft Defender usługi.

Jeśli zostanie wyświetlony komunikat o błędzie, Microsoft 365 Defender szczegółowe wyjaśnienie przyczyny problemu i zostaną podane odpowiednie linki.

## <a name="no-subscriptions-found"></a>Nie znaleziono subskrypcji

Jeśli podczas uzyskiwania dostępu Microsoft 365 Defender zostanie wyświetlony komunikat Nie  znaleziono subskrypcji, oznacza to, że Azure Active Directory (Azure AD) używany do logowania użytkownika do portalu, nie ma licencji Ochrona punktu końcowego w usłudze Microsoft Defender subskrypcji.

Potencjalne powody:

- Licencje Windows E5 i Office E5 to oddzielne licencje.
- Licencja została zakupiona, ale nie jest aprowowana w tym wystąpieniu usługi Azure AD.
  - Może to być problem z inicjowaniem obsługi licencji.
  - Może to być przypadkowo aprowizowana licencja na inny Microsoft Azure AD niż ta używana do uwierzytelniania w usłudze.

W obu przypadkach należy skontaktować się z pomocą techniczną firmy Microsoft na stronie Ogólne [Ochrona punktu końcowego w usłudze Microsoft Defender pomocy technicznej lub](https://support.microsoft.com/getsupport?wf=0&tenant=ClassicCommercial&oaspworkflow=start_1.0.0.0&locale=en-us&supportregion=en-us&pesid=16055&ccsid=636419533611396913) [Pomoc techniczna w związku z licencją volume license](https://www.microsoft.com/licensing/servicecenter/Help/Contact.aspx).

:::image type="content" source="images/atp-no-subscriptions-found.png" alt-text="Strona Nie znaleziono subskrypcji" lightbox="images/atp-no-subscriptions-found.png":::

## <a name="your-subscription-has-expired"></a>Twoja subskrypcja wygasła

Jeśli podczas uzyskiwania dostępu Microsoft 365 Defender się komunikat Twoja subskrypcja wygasła, Twoja subskrypcja usługi online wygasła. Ochrona punktu końcowego w usłudze Microsoft Defender, tak jak każda inna subskrypcja usługi online, ma datę wygaśnięcia.

W dowolnym momencie możesz odnowić lub przedłużyć licencję. Podczas uzyskiwania dostępu do portalu po dacie wygaśnięcia zostanie  wyświetlony komunikat Twoja subskrypcja zostanie wyświetlony komunikat z opcją pobrania pakietu wynosięcia urządzenia, jeśli nie odnowisz licencji.

> [!NOTE]
> Ze względów bezpieczeństwa pakiet używany na urządzeniach offboardowych wygaśnie po 30 dniach od daty jego pobrania. Pakiety wynoszące wygasłe wysłane na urządzenie zostaną odrzucone. Podczas pobierania pakietu wynegocjowego zostaniesz o nim powiadomiony(-a) o dacie wygaśnięcia pakietów, a także w nazwie pakietu.

:::image type="content" source="images/atp-subscription-expired.png" alt-text="Subskrypcja wygasła komunikat z powiadomieniem" lightbox="images/atp-subscription-expired.png":::

## <a name="you-are-not-authorized-to-access-the-portal"></a>Nie masz uprawnień do uzyskiwania dostępu do portalu

Jeśli otrzymasz powiadomienie Nie masz uprawnień do uzyskiwania dostępu do **portalu, musisz** pamiętać, że program Ochrona punktu końcowego w usłudze Microsoft Defender jest produktem monitorowania zabezpieczeń, badania zdarzeń i reagowania na incydenty, a w związku z tym dostęp do niego jest ograniczony i kontrolowany przez użytkownika.
Aby uzyskać więcej informacji, zobacz [**Przypisywanie dostępu użytkownika do portalu**](/windows/threat-protection/windows-defender-atp/assign-portal-access-windows-defender-advanced-threat-protection).

:::image type="content" source="images/atp-not-authorized-to-access-portal.png" alt-text="Dostęp jest niedozwolone komunikat z powiadomieniem" lightbox="images/atp-not-authorized-to-access-portal.png":::

## <a name="data-currently-isnt-available-on-some-sections-of-the-portal"></a>Dane nie są obecnie dostępne w niektórych sekcjach portalu

Jeśli pulpit nawigacyjny portalu i inne sekcje zawierają komunikat o błędzie, taki jak "Dane obecnie nie są dostępne":

:::image type="content" source="images/atp-data-not-available.png" alt-text="Brak możliwości dostępu do komunikat z powiadomieniem" lightbox="images/atp-data-not-available.png":::

Musisz zezwolić na wszystkie `security.windows.com` poddomeny w jej obszarze w przeglądarce internetowej. Na przykład `*.security.windows.com`.

## <a name="portal-communication-issues"></a>Problemy z komunikacją w portalu

Jeśli wystąpią problemy z uzyskaniem dostępu do portalu, brakjącymi danymi lub ograniczeniem dostępu do części portalu, musisz sprawdzić, czy następujące adresy URL są dozwolone i otwarte do komunikacji.

- `*.blob.core.windows.net`
- `crl.microsoft.com`
- `https://*.microsoftonline-p.com`
- `https://*.security.microsoft.com`
- `https://automatediracs-eus-prd.security.microsoft.com`
- `https://login.microsoftonline.com`
- `https://login.windows.net`
- `https://onboardingpackagescusprd.blob.core.windows.net`
- `https://secure.aadcdn.microsoftonline-p.com`
- `https://security.microsoft.com`
- `https://static2.sharepointonline.com`
