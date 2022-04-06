---
title: Adres naruszonych kont użytkowników przy użyciu automatycznego badania i odpowiedzi
keywords: AIR, autoIR, Ochrona punktu końcowego w usłudze Microsoft Defender, zautomatyzowane, badania, odpowiedzi, działania naprawcze, zagrożenia, zaawansowane, zagrożenia, ochrona, naruszone
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection: M365-security-compliance
ms.custom: ''
ms.date: 06/10/2021
description: Dowiedz się, jak przyspieszyć proces wykrywania naruszonych kont użytkowników i rozwiązywania związanych z nim problemów za pomocą funkcji automatycznego badania i odpowiedzi w programie Ochrona usługi Office 365 w usłudze Microsoft Defender planie 2.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c1488598eb3a198a70997e755fe77a8a0c97e1c0
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474367"
---
# <a name="address-compromised-user-accounts-with-automated-investigation-and-response"></a>Adres naruszonych kont użytkowników przy użyciu automatycznego badania i odpowiedzi

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)


[Ochrona usługi Office 365 w usłudze Microsoft Defender Plan 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) obejmuje zaawansowane funkcje automatycznego [badania i odpowiedzi](office-365-air.md) (AIR). Takie możliwości mogą zaoszczędzić wiele czasu i wysiłku zespołu operacyjnego w związku z zagrożeniami. Firma Microsoft będzie nadal ulepszać funkcje zabezpieczeń. Ostatnio funkcje AIR zostały rozszerzone tak, aby zawierały naruszony podręcznik zabezpieczeń użytkowników (obecnie dostępny w wersji Preview). Przeczytaj ten artykuł, aby dowiedzieć się więcej o podręczniku zabezpieczeń użytkownika, który został naruszony. Aby uzyskać [więcej szczegółowych informacji](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Speed-up-time-to-detect-and-respond-to-user-compromise-and-limit/ba-p/977053), zapoznaj się z wpisem w blogu Przyspieszyć wykrywanie naruszenia bezpieczeństwa użytkowników i ograniczanie zakresu naruszenia Ochrona usługi Office 365 w usłudze Microsoft Defender blogu.

![Zautomatyzowane badanie w przypadku naruszonego użytkownika.](/microsoft-365/media/office365atp-compduserinvestigation.jpg)

Podręcznik zabezpieczeń użytkowników, w przypadku których naruszono zabezpieczenia, umożliwia zespołowi zabezpieczeń w organizacji:

- Przyspieszyć wykrywanie naruszonych kont użytkowników;
- ograniczanie zakresu naruszenia bezpieczeństwa w przypadku naruszenia konta; i
- Skuteczniej i skuteczniej odpowiadaj na naruszonych użytkowników.

## <a name="compromised-user-alerts"></a>Naruszone alerty użytkownika

W przypadku naruszenia konta użytkownika występują nietypowe lub nietypowe zachowania. Na przykład wiadomości wyłudzają informacje i spam mogą być wysyłane wewnętrznie z zaufanego konta użytkownika. Ochrona usługi Office 365 w usłudze Defender wykryć takie anomalie w wzorcach poczty e-mail i aktywności współpracy w ramach Office 365. Gdy tak się stanie, alerty są wyzwalane i rozpoczyna się proces ograniczania zagrożeń.

Oto przykładowy alert, który został wyzwolony z powodu podejrzanego wysyłania wiadomości e-mail:

![Alert wyzwolony z powodu podejrzanego wysyłania wiadomości e-mail.](/microsoft-365/media/office365atp-suspiciousemailsendalert.jpg)

Oto przykład alertu, który został wyzwolony po osiągnięciu limitu wysyłania dla użytkownika:

![Alert wyzwalany przez osiągnięto limit wysyłania.](/microsoft-365/media/office365atp-sendinglimitreached.jpg)

## <a name="investigate-and-respond-to-a-compromised-user"></a>Badanie naruszonego użytkownika i odpowiadanie na nie

Gdy konto użytkownika zostanie naruszone, są wyzwolone alerty. W niektórych przypadkach to konto użytkownika jest zablokowane i nie może wysyłać kolejnych wiadomości e-mail, dopóki nie zostanie rozwiązany przez zespół operacyjny zabezpieczeń Twojej organizacji. W innych przypadkach rozpoczyna się zautomatyzowane badanie, co może spowodować zalecane działania, które powinien podjąć Twój zespół zabezpieczeń.

- [Wyświetlanie i badanie użytkowników z ograniczeniami](#view-and-investigate-restricted-users)

- [Wyświetlanie szczegółów zautomatyzowanych badań](#view-details-about-automated-investigations)

> [!IMPORTANT]
> Musisz mieć odpowiednie uprawnienia, aby wykonać następujące zadania. Zobacz [Wymagane uprawnienia do używania funkcji AIR](office-365-air.md#required-permissions-to-use-air-capabilities).

### <a name="view-and-investigate-restricted-users"></a>Wyświetlanie i badanie użytkowników z ograniczeniami

Dostępnych jest kilka opcji przechodzenia do listy użytkowników z ograniczeniami. Na przykład w portalu Microsoft 365 Defender można przejść do tematu Współpraca za pomocą poczty e-mail &  \> **przejrzeć użytkowników** \> **z ograniczeniami**. W poniższej procedurze opisano nawigację za pomocą pulpitu nawigacyjnego **alertów** , który jest dobrym sposobem na wyświetlanie różnych rodzajów alertów, które mogły zostać wyzwolone.

1. Otwórz portal Microsoft 365 Defender i <https://security.microsoft.com> przejdź do **tematu Alerty o & zdarzeniach**\>. Aby przejść bezpośrednio do strony **Alerty**, użyj .<https://security.microsoft.com/alerts>

2. Na stronie **Alerty** filtruj wyniki według okresu i zasad o nazwie Użytkownik **ograniczony do wysyłania wiadomości e-mail**.

   :::image type="content" source="../../media/m365-sc-alerts-page-with-restricted-user.png" alt-text="Strona Alerty w portalu Microsoft 365 Defender z filtrami dla użytkowników z ograniczeniami" lightbox="../../media/m365-sc-alerts-page-with-restricted-user.png":::

3. Jeśli wybierzesz wpis, klikając nazwę, zostanie otwarta strona Użytkownik  z ograniczeniami do wysyłania wiadomości e-mail z dodatkowymi szczegółami do przejrzenia. Obok **przycisku Zarządzaj alertem** możesz kliknąć ikonę ![Więcej opcji.](../../media/m365-cc-sc-more-actions-icon.png) **Więcej opcji**, a następnie wybierz **pozycję Wyświetl ograniczone szczegóły użytkownika**, aby  przejść do strony Użytkownicy z ograniczeniami, gdzie możesz [zwolnić użytkownika z ograniczeniami](removing-user-from-restricted-users-portal-after-spam.md).

  :::image type="content" source="../../media/m365-sc-alerts-user-restricted-from-sending-email-page.png" alt-text="Użytkownik z ograniczonymi możliwościami wysyłania wiadomości e-mail" lightbox="../../media/m365-sc-alerts-user-restricted-from-sending-email-page.png":::

### <a name="view-details-about-automated-investigations"></a>Wyświetlanie szczegółów zautomatyzowanych badań

Gdy zostanie rozpoczęte zautomatyzowane badanie, możesz wyświetlić jego szczegóły i wyniki w Centrum zgodności & zabezpieczeń. Przejdź do **strony Badania** \> **zarządzania zagrożeniami**, a następnie wybierz badanie, aby wyświetlić jego szczegóły.

Aby dowiedzieć się więcej, [zobacz Wyświetlanie szczegółów badania](air-view-investigation-results.md).

## <a name="keep-the-following-points-in-mind"></a>Należy pamiętać o następujących kwestiach

- **Bądź na wierzchu alertów**. Jak wiadomo, im więcej łamania zabezpieczeń, tym większy jest potencjalny wpływ na odbiorców i koszty w organizacji, klientach i partnerach. Wczesne wykrywanie i terminowe reagowanie mają kluczowe znaczenie dla ograniczania zagrożeń, zwłaszcza w przypadku naruszenia bezpieczeństwa konta użytkownika.

- **Automatyzacja pomaga, ale nie zastępuje zespołu operacyjnego zabezpieczeń**. Funkcje automatycznego badania i reakcji mogą wcześniej wykryć naruszonego użytkownika, ale zespół operacyjny ds. zabezpieczeń prawdopodobnie będzie musiał zaangażować się i wykonać pewne działania naprawcze i badania. Potrzebujesz pomocy w tym? Zobacz [Przeglądanie i zatwierdzanie akcji](air-review-approve-pending-completed-actions.md).

- **Jako jedyny wskaźnik nie należy polegać na podejrzanych alertach logowania**. Jeśli konto użytkownika zostanie naruszone, może (ale nie musi) spowodować wyzwolenie podejrzanego alertu logowania. Czasami jest to seria działań, która występuje po naruszoniu konta, co powoduje wyzwolenie alertu. Chcesz dowiedzieć się więcej o alertach? Zobacz [Zasady alertów](../../compliance/alert-policies.md).

## <a name="next-steps"></a>Następne kroki

- [Przejrzyj wymagane uprawnienia do korzystania z funkcji AIR](office-365-air.md#required-permissions-to-use-air-capabilities)

- [Znajdowanie i badanie złośliwych wiadomości e-mail w programie Office 365](investigate-malicious-email-that-was-delivered.md)

- [Informacje o programie AIR w programie Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)

- [Odwiedź Microsoft 365 Przewodnik po aktualizacjach, aby zobaczyć, co zostanie wkrótce wyedytować](https://www.microsoft.com/microsoft-365/roadmap?filters=)