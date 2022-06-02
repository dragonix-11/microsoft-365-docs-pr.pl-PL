---
title: Omówienie wdrażania standardowych konfiguracji dzierżawy przy użyciu Microsoft 365 Lighthouse planów bazowych
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: W przypadku dostawców usług zarządzanych korzystających z Microsoft 365 Lighthouse dowiedz się więcej na temat wdrażania standardowych konfiguracji dzierżawy przy użyciu punktów odniesienia.
ms.openlocfilehash: 7cdae46105ad225a284bf0ffa8860ad36ffb8691
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2022
ms.locfileid: "65839848"
---
# <a name="overview-of-using-microsoft-365-lighthouse-baselines-to-deploy-standard-tenant-configurations"></a>Omówienie wdrażania standardowych konfiguracji dzierżawy przy użyciu Microsoft 365 Lighthouse planów bazowych 

Microsoft 365 Lighthouse punkty odniesienia zapewniają powtarzalny i skalowalny sposób zarządzania Microsoft 365 ustawieniami zabezpieczeń w wielu dzierżawach klientów. Linie bazowe zapewniają standardowe konfiguracje dzierżaw, które wdrażają podstawowe zasady zabezpieczeń i standardy zgodności, które zapewniają bezpieczeństwo użytkowników, urządzeń i danych dzierżawców.

Możesz wyświetlić domyślny punkt odniesienia i jego kroki wdrażania z poziomu usługi Lighthouse. Aby zastosować punkt odniesienia do dzierżawy, wybierz pozycję **Dzierżawy** w okienku nawigacji po lewej stronie, a następnie wybierz dzierżawę. Następnie przejdź do karty **Plany wdrożenia** , aby rozpocząć wdrażanie.

## <a name="lighthouse-baseline"></a>Punkt odniesienia latarni morskiej

Konfiguracje punktu odniesienia usługi Lighthouse zostały zaprojektowane tak, aby upewnić się, że wszystkie zarządzane dzierżawy są bezpieczne i zgodne. Wybierz pozycję **Punkty odniesienia** w okienku nawigacji po lewej stronie, aby wyświetlić domyślny punkt odniesienia, który ma zastosowanie do wszystkich dzierżaw.  Aby wyświetlić kroki wdrażania zawarte w domyślnym punkcie odniesienia, wybierz pozycję **Wyświetl punkt odniesienia** , aby otworzyć domyślną stronę **punktu odniesienia** . Wybierz dowolny z kroków wdrażania, aby wyświetlić szczegóły wdrożenia i wpływ na użytkownika.

:::image type="content" source="../media/m365-lighthouse-deploy-baselines/default-baseline-page.png" alt-text="Zrzut ekranu przedstawiający domyślną stronę punktu odniesienia.":::

### <a name="default-lighthouse-configurations"></a>Domyślne konfiguracje usługi Lighthouse

| Konfiguracja punktu odniesienia | Opis |
|--|--|
| Wymagaj uwierzytelniania wieloskładnikowego dla administratorów | Zasady dostępu warunkowego wymagające uwierzytelniania wieloskładnikowego dla wszystkich administratorów. Jest to wymagane dla wszystkich aplikacji w chmurze. Aby uzyskać więcej informacji na temat tego punktu odniesienia, zobacz [Dostęp warunkowy: Wymagaj uwierzytelniania wieloskładnikowego dla wszystkich administratorów](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa).|
| Wymagaj uwierzytelniania wieloskładnikowego dla użytkowników końcowych | Zasady dostępu warunkowego, które wymagają uwierzytelniania wieloskładnikowego dla wszystkich użytkowników.  Jest to wymagane dla wszystkich aplikacji w chmurze. Aby uzyskać więcej informacji na temat tego punktu odniesienia, zobacz [Dostęp warunkowy: Wymagaj uwierzytelniania wieloskładnikowego dla wszystkich użytkowników](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa). |
| Blokowanie starszego uwierzytelniania | Zasady dostępu warunkowego do blokowania starszego uwierzytelniania klienta. Aby uzyskać więcej informacji na temat tego punktu odniesienia, zobacz [Blokuj starsze uwierzytelnianie, aby Azure AD przy użyciu dostępu warunkowego](/azure/active-directory/conditional-access/block-legacy-authentication).|
| Konfigurowanie rejestracji urządzeń | Rejestrowanie urządzeń w celu umożliwienia rejestrowania urządzeń dzierżawy w Microsoft Endpoint Manager. W tym celu należy skonfigurować automatyczne rejestrowanie między Azure Active Directory a Microsoft Endpoint Manager. Aby uzyskać więcej informacji na temat tego punktu odniesienia, zobacz [Konfigurowanie rejestracji dla urządzeń Windows](/mem/intune/enrollment/windows-enroll). |
| Konfigurowanie Exchange Online Protection i Ochrona usługi Office 365 w usłudze Microsoft Defender | Zasady stosowania zalecanych zasad ochrony przed spamem, ochrony przed złośliwym oprogramowaniem, ochrony przed wyłudzaniem informacji, bezpiecznych linków i zasad bezpiecznego załącznika do dzierżaw Exchange Online skrzynek pocztowych. |
| Konfigurowanie Program antywirusowy Microsoft Defender dla Windows 10 i nowszych | Profil konfiguracji urządzenia dla urządzeń Windows ze wstępnie skonfigurowanymi ustawieniami Program antywirusowy Microsoft Defender. Aby uzyskać więcej informacji na temat tego punktu odniesienia, zobacz [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender w Intune](/mem/intune/protect/advanced-threat-protection-configure).|
| Konfigurowanie Zapora Microsoft Defender dla Windows 10 i nowszych | Zasady zapory ułatwiające zabezpieczanie urządzeń przez zapobieganie niepożądanemu i nieautoryzowanemu ruchowi sieciowemu. Aby uzyskać więcej informacji na temat tego punktu odniesienia, zobacz [Najlepsze rozwiązania dotyczące konfigurowania Zapora Windows Defender](/windows/security/threat-protection/windows-firewall/best-practices-configuring).  |
| Konfigurowanie zasad zgodności urządzeń dla Windows 10 i nowszych | Zasady Windows urządzenia ze wstępnie skonfigurowanymi ustawieniami spełniającymi podstawowe wymagania dotyczące zgodności. Aby uzyskać więcej informacji na temat tego punktu odniesienia, zobacz [Dostęp warunkowy: Wymagaj zgodnego lub hybrydowego urządzenia przyłączonych do Azure AD](/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device). |

## <a name="deployment-plans"></a>Plany wdrażania

Każda aktywna dzierżawa ma plan wdrożenia, który obejmuje kroki wdrażania z punktu odniesienia Microsoft 365 Lighthouse. Aby uzyskać dostęp do planu wdrażania dzierżawy, wybierz aktywną dzierżawę z listy na stronie **Dzierżawy** , a następnie wybierz kartę **Plan wdrożenia** .

:::image type="content" source="../media/m365-lighthouse-deploy-baselines/deployment-plan-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Plan wdrożenia.":::

Karta Plan wdrożenia zawiera następujące informacje:


|Kolumna  |Opis  |
|---------|---------|
|Krok wdrożenia     |  Opis kroku wdrożenia.       |
|Stan     |Stan kroku wdrożenia.         |
|Linii bazowej     |Punkt odniesienia, z którego pochodzi krok wdrożenia.         |
|Kategoria     | Czy krok wdrożenia jest skojarzony z zarządzaniem urządzeniami, tożsamością czy danymi.        |
|Ostatnia aktualizacja    | Data ostatniej aktualizacji kroku wdrożenia.        |


Karta Plan wdrożenia zawiera również następujące opcje:

- **Eksportu:** Wybierz, aby wyeksportować dane kroku wdrożenia do pliku wartości rozdzielanych przecinkami Excel (.csv).
- **Odświeżania:** Wybierz, aby pobrać najbardziej aktualne dane kroków wdrażania.
- **Szukaj:** Wprowadź słowa kluczowe, aby szybko zlokalizować określony krok wdrożenia na liście.

## <a name="deployment-steps-and-processes"></a>Kroki i procesy wdrażania

Plan wdrażania każdej dzierżawy obejmuje kroki wdrażania z punktu odniesienia Microsoft 365 Lighthouse. Każdy krok wdrażania obejmuje co najmniej jeden proces, który należy ukończyć. Gdy nowa dzierżawa stanie się aktywna, należy ukończyć działania wdrażania skojarzone z krokami i procesami wdrażania.

Dla każdego kroku wdrażania można wykonać następujące akcje:

|Akcja  |Opis  |
|---------|---------|
| Udostępnianie    |  Umożliwia udostępnianie zawartości kroku wdrożenia za pośrednictwem linku lub wiadomości e-mail.    |
| Przeglądanie i wdrażanie    |  Umożliwia użytkownikowi: <ul><li>Jeśli jest to obsługiwane, porównaj ustawienia konfiguracji w kroku wdrażania z ustawieniami w istniejących zasadach bez wdrażania ustawień w dzierżawie.<br>Poniższe kroki wdrażania obsługują porównanie:</br><ul><li>Konfigurowanie zasad zgodności urządzeń dla Windows 10 i nowszych</li><li>Wymagaj uwierzytelniania wieloskładnikowego dla użytkowników końcowych</li><li>Wymagaj uwierzytelniania wieloskładnikowego dla administratorów</li><li>Blokowanie starszego uwierzytelniania</li></ul></li> <li>Wdróż ustawienia konfiguracji w dzierżawie.</li></ul>**Uwaga:** Kroki, które nie obsługują możliwości porównywania bez wdrażania ustawień w dzierżawie, umożliwią zapoznanie się z ustawieniami konfiguracji i ich wdrożenie.|
| Aktualizowanie stanu planu akcji    |  Umożliwia użytkownikowi zgłaszanie stanu planu działania dla kroku wdrażania.      |

## <a name="related-content"></a>Zawartość pokrewna

[Wdrażanie Microsoft 365 Lighthouse punktów odniesienia](m365-lighthouse-deploy-baselines.md) (artykuł)\
[Typowe zasady dostępu warunkowego](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) (artykuł)\
[Microsoft 365 Lighthouse często zadawane pytania](m365-lighthouse-faq.yml) (artykuł)
