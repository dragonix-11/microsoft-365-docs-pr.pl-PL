---
title: Omówienie strony Użytkownicy w Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: ragovind
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
description: W przypadku dostawców usług zarządzanych korzystających z Microsoft 365 Lighthouse zapoznaj się ze stroną Użytkownicy.
ms.openlocfilehash: d817ab74d6dd24e644561684073189e68cf7e072
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66007289"
---
# <a name="overview-of-the-users-page-in-microsoft-365-lighthouse"></a>Omówienie strony Użytkownicy w Microsoft 365 Lighthouse 

Microsoft 365 Lighthouse umożliwia zarządzanie użytkownikami na kontach dzierżawy klienta, wybierając pozycję **Użytkownicy** w okienku nawigacji po lewej stronie, aby otworzyć stronę Użytkownicy. Na tej stronie można wyszukiwać użytkowników oraz oceniać stan zabezpieczeń kont użytkowników i działać na ich podstawie. Możesz również wyświetlić szczegółowe informacje na temat ryzykownych użytkowników oraz stanu uwierzytelniania wieloskładnikowego i samoobsługowego resetowania haseł.  
  
## <a name="search-users-tab"></a>Karta Wyszukaj użytkowników  
  
Na karcie Wyszukaj użytkowników możesz szybko wyszukiwać konkretnych użytkowników w dzierżawach i wykonywać podstawowe akcje zarządzania użytkownikami, takie jak resetowanie hasła konta.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-search-users-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Wyszukaj użytkowników.":::

## <a name="risky-users-tab"></a>Karta Ryzykowni użytkownicy

Na karcie Ryzykowni użytkownicy są wyświetlane konta użytkowników w dzierżawach, które zostały oflagowane pod kątem ryzykownego zachowania. Wybierz dowolnego z użytkowników, aby wyświetlić więcej informacji na temat wykrytego ryzyka lub ograniczyć ryzyko, resetując hasło użytkownika lub blokując logowanie. Aby uzyskać więcej informacji na temat typów ryzyka i wykrywania, zobacz [Co to jest ryzyko?](/azure/active-directory/identity-protection/concept-identity-protection-risks).

Karta Ryzykowni użytkownicy zawiera również następujące opcje:
- **Eksportu:** Wybierz, aby wyeksportować dane zgodności urządzeń do pliku Excel wartości rozdzielanych przecinkami (.csv).
- **Odświeżania:** Wybierz, aby pobrać najbardziej aktualne dane zgodności urządzeń.
- **Potwierdź, że bezpieczeństwo użytkowników zostało naruszone:** Wybierz, aby potwierdzić, że użytkownik został naruszona.
- **Odrzucanie ryzyka związanego z użytkownikami:** Wybierz, aby odrzucić ryzyko użytkownika.  
- **Resetowanie hasła:** Wybierz, aby zmienić lub zresetować hasło użytkownika.
- **Blokuj logowanie:** Wybierz opcję , aby uniemożliwić użytkownikom logowanie się jako ten użytkownik.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-risky-users-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Ryzykowni użytkownicy.":::

## <a name="multifactor-authentication-tab"></a>Karta Uwierzytelnianie wieloskładnikowe

Karta Uwierzytelnianie wieloskładnikowe zawiera szczegółowe informacje na temat stanu włączania uwierzytelniania wieloskładnikowego (MFA) w dzierżawach. Wybierz dowolną dzierżawę na liście, aby wyświetlić więcej szczegółów dotyczących tej dzierżawy, w tym informacje o tym, które zasady dostępu warunkowego wymagające uwierzytelniania wieloskładnikowego zostały już skonfigurowane i którzy użytkownicy nie zarejestrowali się jeszcze w usłudze MFA.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-mfa-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Uwierzytelnianie wieloskładnikowe.":::

## <a name="password-reset-tab"></a>Karta Resetowanie hasła

Karta Resetowanie hasła zawiera szczegółowe informacje o stanie włączania samoobsługowego resetowania haseł w dzierżawach. Zapewnia również wgląd w użytkowników, którzy są włączone, ale nadal muszą się zarejestrować, zanim będą mogli samodzielnie zresetować swoje hasło.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-password-reset-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Resetowanie hasła.":::

## <a name="related-content"></a>Zawartość pokrewna

[Microsoft 365 Lighthouse omówienie strony zgodności urządzeń](m365-lighthouse-device-compliance-page-overview.md) (artykuł)\
[Microsoft 365 Lighthouse często zadawane pytania](m365-lighthouse-faq.yml) (artykuł)
