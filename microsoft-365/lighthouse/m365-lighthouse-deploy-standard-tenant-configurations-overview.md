---
title: Omówienie wdrażania standardowych konfiguracji dzierżawy przy użyciu planu bazowego
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
description: W przypadku dostawców usług zarządzanych (MSP) używających Microsoft 365 Lighthouse informacji o wdrażaniu standardowych konfiguracji dzierżawy przy użyciu planu bazowego.
ms.openlocfilehash: 643bb962277d30caf8ea067b9276a5986af8914f
ms.sourcegitcommit: 8423f47fce3905a48db9daefe69c21c841da43a0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2022
ms.locfileid: "63504524"
---
# <a name="overview-of-using-baselines-to-deploy-standard-tenant-configurations"></a>Omówienie wdrażania standardowych konfiguracji dzierżawy przy użyciu planu bazowego 

Microsoft 365 Lighthouse bazowe zapewniają powtarzalny i skalowalny sposób zarządzania ustawieniami zabezpieczeń Microsoft 365 w wielu dzierżawach klientów. Linie bazowe zapewniają standardowe konfiguracje dzierżaw, które wdrażają podstawowe zasady zabezpieczeń i standardy zgodności, które zapewniają bezpieczeństwo użytkowników, urządzeń i danych dzierżawcy.

Domyślny plan bazowy i kroki jego wdrożenia możesz wyświetlić z poziomu usługi Lighthouse. Aby zastosować plan bazowy do dzierżawy, wybierz pozycję **Dzierżawy** w lewym okienku nawigacji, a następnie wybierz dzierżawę. Następnie przejdź do karty **Plany wdrażania** , aby rozpocząć wdrażanie.

## <a name="lighthouse-baseline"></a>Linia bazowa latarni morskiej

Konfiguracje bazowe usługi Lighthouse zaprojektowano tak, aby zapewnić, że wszystkie zarządzane dzierżawy są bezpieczne i zgodne. Wybierz **pozycję Linie bazowe** w lewym okienku nawigacji, aby wyświetlić domyślny plan bazowy, który dotyczy wszystkich dzierżaw.  Aby wyświetlić kroki wdrażania zawarte w domyślnym planie bazowym, wybierz pozycję **Wyświetl** plan bazowy, aby otworzyć stronę domyślnego planu bazowego. Wybierz dowolny z kroków wdrażania, aby wyświetlić szczegóły wdrożenia i wpływ na użytkowników.

:::image type="content" source="../media/m365-lighthouse-deploy-baselines/default-baseline-page.png" alt-text="Zrzut ekranu przedstawiający stronę Domyślny plan bazowy.":::

### <a name="default-lighthouse-configurations"></a>Domyślne konfiguracje latarni morskiej

| Konfiguracja planu bazowego | Opis |
|--|--|
| Wymaganie uwierzytelniania wieloskładnikowego dla administratorów | Zasady dostępu warunkowego wymagające uwierzytelniania wieloskładnikowego dla wszystkich administratorów. Jest ona wymagana dla wszystkich aplikacji w chmurze. Aby uzyskać więcej informacji o tym planie bazowym, zobacz [Dostęp warunkowy: Wymaganie uwierzytelniania MFA dla wszystkich administratorów](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa).|
| Wymaganie uwierzytelniania wieloskładnikowego dla użytkowników końcowych | Zasady dostępu warunkowego wymagające uwierzytelniania wieloskładnikowego dla wszystkich użytkowników.  Jest ona wymagana dla wszystkich aplikacji w chmurze. Aby uzyskać więcej informacji o tym planie bazowym, zobacz [Dostęp warunkowy: Wymaganie uwierzytelniania MFA dla wszystkich użytkowników](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa). |
| Blokowanie starszego uwierzytelniania | Zasady dostępu warunkowego do blokowania starszego uwierzytelniania klienta. Aby uzyskać więcej informacji na temat tego planu bazowego, zobacz [Blokowanie starszego uwierzytelniania w usłudze Azure AD z dostępem warunkowym](/azure/active-directory/conditional-access/block-legacy-authentication).|
| Konfigurowanie rejestrowania urządzenia | Rejestracja urządzeń w celu umożliwienia urządzeniu dzierżawcy zarejestrowania się w Microsoft Endpoint Manager. W tym celu należy skonfigurować automatyczne rejestrowanie między Azure Active Directory a Microsoft Endpoint Manager. Aby uzyskać więcej informacji o tym planie bazowym, [zobacz Konfigurowanie rejestracji Windows urządzeniach](/mem/intune/enrollment/windows-enroll). |
| Konfigurowanie Program antywirusowy Microsoft Defender dla Windows 10 i nowszych | Profil konfiguracji urządzenia dla Windows urządzeń ze wstępnie skonfigurowanymi Program antywirusowy Microsoft Defender ustawieniami. Aby uzyskać więcej informacji na temat tego planu bazowego, [zobacz Konfigurowanie programu Microsoft Defender dla punktu końcowego w usłudze Intune](/mem/intune/protect/advanced-threat-protection-configure).|
| Konfigurowanie Zapory programu Microsoft Defender do Windows 10 i nowszych | Zasady zapory ułatwiające zabezpieczanie urządzeń przez zapobieganie niechcianym i nieautoryzowanym ruchom sieciowym. Aby uzyskać więcej informacji na temat tego planu bazowego, zobacz Najlepsze rozwiązania dotyczące [konfigurowania Windows Defender sieciowej](/windows/security/threat-protection/windows-firewall/best-practices-configuring).  |
| Konfigurowanie zasad zgodności urządzenia dla Windows 10 i nowszych | Zasady Windows urządzenia ze wstępnie skonfigurowanymi ustawieniami w celu spełnienia podstawowych wymagań dotyczących zgodności. Aby uzyskać więcej informacji na temat tego planu bazowego, zobacz [Dostęp warunkowy: wymaganie zgodnego lub hybrydowego urządzenia połączonego z usługą Azure AD](/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device). |

## <a name="deployment-plans"></a>Plany wdrażania

Każda aktywna dzierżawa ma plan wdrożenia, który zawiera kroki wdrażania z Microsoft 365 Lighthouse bazowego. Aby uzyskać dostęp do planu wdrażania dzierżawy, wybierz aktywną dzierżawę z listy na  stronie Dzierżawcy, a następnie wybierz **kartę Plan** wdrażania.

:::image type="content" source="../media/m365-lighthouse-deploy-baselines/deployment-plan-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Plan wdrażania.":::

Karta Plan wdrażania zawiera następujące informacje:


|Kolumna  |Opis  |
|---------|---------|
|Krok wdrażania     |  Opis etapu wdrażania.       |
|Stan     |Stan kroku wdrażania.         |
|Plan bazowy     |Plan bazowy, na podstawie którego pochodzi etap wdrożenia.         |
|Kategoria     | Czy etap wdrażania jest skojarzony z zarządzaniem urządzeniami, tożsamością lub danymi.        |
|Ostatnia aktualizacja    | Data ostatniej aktualizacji kroku wdrażania.        |


Karta Plan wdrażania zawiera również następujące opcje:

- **Eksportowanie:** Wybierz, aby wyeksportować dane o krokach wdrożenia Excel pliku wartości rozdzielanych przecinkami (.csv).
- **Odświeżanie:** Wybierz, aby pobrać najnowsze dane o krokach wdrożenia.
- **Wyszukiwanie:** Wprowadź słowa kluczowe, aby szybko znaleźć określony krok wdrożenia na liście.

## <a name="deployment-steps-and-processes"></a>Etapy i procesy wdrażania

Plan wdrażania każdej dzierżawy zawiera kroki wdrażania z Microsoft 365 Lighthouse bazowego. Każdy krok wdrożenia składa się z jednego lub większej liczby procesów, które muszą zostać ukończone, aby spełnić wymagania kroku wdrażania. Gdy nowa dzierżawa stanie się aktywna, musisz ukończyć działania wdrażania skojarzone z procesami i krokami wdrażania.

W każdym kroku wdrażania możesz podjąć następujące czynności:

|Akcja  |Opis  |
|---------|---------|
| Udostępnianie    |  Umożliwia udostępnieniu zawartości Kroku wdrażania za pomocą linku lub wiadomości e-mail.    |
| Przeglądanie i wdrażanie    |  Umożliwia użytkownikowi: <ul><li>Jeśli ta konfiguracja jest obsługiwana, porównaj ustawienia konfiguracyjne w kroku wdrażania z ustawieniami we wszystkich istniejących zasadach bez wdrażania ustawień w dzierżawie.<br>Porównanie kroków wdrażania jest następujące:</br><ul><li>Konfigurowanie zasad zgodności urządzenia dla Windows 10 i nowszych</li><li>Wymaganie uwierzytelniania MFA dla użytkowników końcowych</li><li>Wymaganie uwierzytelniania wieloskładnikowego dla administratorów</li><li>Blokowanie starszego uwierzytelniania</li></ul></li> <li>Wdeksuj ustawienia konfiguracji w dzierżawie.</li></ul>**Uwaga:** Kroki, które nie obsługują porównywania bez wdrażania ustawień w dzierżawie, umożliwią sprawdzenie ustawień konfiguracji i ich wdrożenie.|
| Aktualizowanie stanu planu akcji    |  Umożliwia użytkownikowi zgłoszenie stanu planu działań w kroku wdrażania.      |

## <a name="related-content"></a>Zawartość pokrewna

[Wdrażanie Microsoft 365 Lighthouse bazowych](m365-lighthouse-deploy-baselines.md) (artykuł)\
[Typowe zasady dostępu warunkowego](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) (artykuł)\
[Microsoft 365 Lighthouse często zadawane pytania](m365-lighthouse-faq.yml) (artykuł)
