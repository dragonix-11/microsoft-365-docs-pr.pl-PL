---
title: Microsoft 365 Lighthouse użytkowników — omówienie
f1.keywords: NOCSH
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
description: Aby uzyskać informacje na temat dostawców usług zarządzanych (MSP) używających Microsoft 365 Lighthouse, dowiedz się więcej o stronie Użytkownicy.
ms.openlocfilehash: fad5ff4b41b43efb68c7e230401b80e50cea95a4
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63329943"
---
# <a name="microsoft-365-lighthouse-users-page-overview"></a>Microsoft 365 Lighthouse użytkowników — omówienie 

Microsoft 365 Lighthouse umożliwia zarządzanie użytkownikami na kontach dzierżawy klientów, wybierając  pozycję Użytkownicy w lewym okienku nawigacji, aby otworzyć stronę Użytkownicy. Na tej stronie możesz wyszukiwać użytkowników oraz oceniać stan zabezpieczeń kont użytkowników i działać na ich podstawie. Możesz również wyświetlać szczegółowe informacje o ryzykownych użytkownikach oraz o stanie uwierzytelniania wieloskładnikowego i samodzielnego resetowania hasła.  
  
## <a name="search-users-tab"></a>Karta Wyszukaj użytkowników  
  
Na karcie Użytkownicy wyszukiwania możesz szybko wyszukiwać konkretnych użytkowników w wielu dzierżawach i wykonywać podstawowe akcje zarządzania użytkownikami, takie jak resetowanie hasła do konta.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-search-users-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Wyszukaj użytkowników.":::

## <a name="risky-users-tab"></a>Karta Ryzykowni użytkownicy

Karta Ryzykowni użytkownicy zawiera konta użytkowników w dzierżawach, które zostały oflagowane przez ryzykowne zachowanie. Wybierz dowolnego użytkownika, aby wyświetlić więcej informacji o wykrytym czynniku ryzyka lub aby zmniejszyć to ryzyko przez zresetowanie hasła użytkownika lub zablokowanie logowania. Aby uzyskać więcej informacji na temat typów ryzyka i wykrywania, zobacz [Co to jest ryzyko?](/azure/active-directory/identity-protection/concept-identity-protection-risks).

Karta Ryzykowni użytkownicy również zawiera następujące opcje:
- **Eksportowanie:** Wybierz, aby wyeksportować dane zgodności urządzenia do Excel pliku wartości rozdzielanych przecinkami (.csv).
- **Odświeżanie:** Wybierz, aby pobrać najnowsze dane dotyczące zgodności urządzenia.
- **Potwierdź naruszone konta użytkowników:** Wybierz tę pozycję, aby potwierdzić, że użytkownik został naruszony.
- **Odrzucenie ryzyka związanego z użytkownikami:** Wybierz pozycję , aby odrzucić ryzyko użytkownika.  
- **Resetowanie hasła:** Wybierz, aby zmienić lub zresetować hasło użytkownika.
- **Blokowanie logowania:** Wybierz tę opcję, aby uniemożliwić innym użytkownikom logowanie się jako ten użytkownik.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-risky-users-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Ryzykowni użytkownicy.":::

## <a name="multifactor-authentication-tab"></a>Karta Uwierzytelnianie wieloskładnikowe

Karta Uwierzytelnianie wieloskładnikowe zawiera szczegółowe informacje o stanie włączania uwierzytelniania wieloskładnikowego (MFA) w dzierżawach. Wybierz dowolną dzierżawę na liście, aby wyświetlić więcej szczegółów dotyczących tej dzierżawy, w tym zasady dostępu warunkowego wymagające uwierzytelniania MFA, które użytkownicy nie zarejestrowali się jeszcze w celu uwierzytelniania MFA.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-mfa-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Uwierzytelnianie wieloskładnikowe.":::

## <a name="password-reset-tab"></a>Karta Resetowanie hasła

Karta Resetowanie hasła zawiera szczegółowe informacje o stanie włączania funkcji samodzielnego resetowania hasła w dzierżawach. Pozwala również uzyskać szczegółowe informacje o użytkownikach, którzy są włączoni, ale nadal muszą się zarejestrować, aby samodzielnie zresetować swoje hasło.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-password-reset-tab.png" alt-text="Zrzut ekranu przedstawiający kartę Resetowanie hasła.":::

## <a name="related-content"></a>Zawartość pokrewna

[omówienie Microsoft 365 Lighthouse zgodności urządzenia](m365-lighthouse-device-compliance-page-overview.md) (artykuł)\
[Microsoft 365 Lighthouse często zadawane pytania](m365-lighthouse-faq.yml) (artykuł)
