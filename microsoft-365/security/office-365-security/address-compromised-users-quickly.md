---
title: Rozwiązywanie problemów z kontami użytkowników, których zabezpieczenia zostały naruszone, za pomocą zautomatyzowanego badania i odpowiedzi
keywords: AIR, autoIR, Ochrona punktu końcowego w usłudze Microsoft Defender, automated, investigation, response, remediation, threats, advanced, threat, protection, compromised
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
description: Dowiedz się, jak przyspieszyć proces wykrywania i rozwiązywania problemów z kontami użytkowników, których zabezpieczenia zostały naruszone, dzięki możliwościom zautomatyzowanego badania i reagowania w planie Ochrona usługi Office 365 w usłudze Microsoft Defender 2.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a8c78847e36d4a4887c4f7a3c54904cc26a012e5
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65131157"
---
# <a name="address-compromised-user-accounts-with-automated-investigation-and-response"></a>Rozwiązywanie problemów z kontami użytkowników, których zabezpieczenia zostały naruszone, za pomocą zautomatyzowanego badania i odpowiedzi

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) obejmuje zaawansowane możliwości [zautomatyzowanego badania i reagowania](office-365-air.md) (AIR). Takie możliwości mogą zaoszczędzić zespołowi ds. operacji zabezpieczeń dużo czasu i wysiłku w radzeniu sobie z zagrożeniami. Firma Microsoft nadal ulepsza możliwości zabezpieczeń. Ostatnio rozszerzono możliwości funkcji AIR w celu uwzględnienia podręcznika zabezpieczeń użytkowników, który został naruszony (obecnie w wersji zapoznawczej). Przeczytaj ten artykuł, aby dowiedzieć się więcej na temat podręcznika zabezpieczeń użytkowników, które zostały naruszone. Aby uzyskać dodatkowe informacje, zobacz wpis w blogu [Speed up time to detect and respond to user compromise and limit breach scope with Ochrona usługi Office 365 w usłudze Microsoft Defender (Skracanie czasu wykrywania i reagowania na naruszenia zabezpieczeń użytkowników oraz ograniczania zakresu naruszeń przy użyciu Ochrona usługi Office 365 w usłudze Microsoft Defender](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Speed-up-time-to-detect-and-respond-to-user-compromise-and-limit/ba-p/977053)).

![Zautomatyzowane badanie użytkownika z naruszeniem zabezpieczeń.](/microsoft-365/media/office365atp-compduserinvestigation.jpg)

Podręcznik zabezpieczeń użytkownika z naruszeniem zabezpieczeń umożliwia zespołowi ds. zabezpieczeń organizacji:

- Przyspiesz wykrywanie kont użytkowników, których bezpieczeństwo zostało naruszone;
- Ogranicz zakres naruszenia zabezpieczeń w przypadku naruszenia zabezpieczeń konta; I
- Efektywniej i wydajniej reagować na naruszenia zabezpieczeń użytkowników.

## <a name="compromised-user-alerts"></a>Alerty użytkowników, których zabezpieczenia zostały naruszone

Gdy konto użytkownika zostanie naruszone, wystąpią nietypowe lub nietypowe zachowania. Na przykład wiadomości wyłudzające informacje i spam mogą być wysyłane wewnętrznie z zaufanego konta użytkownika. Ochrona usługi Office 365 w usłudze Defender może wykrywać takie anomalie we wzorcach poczty e-mail i działaniach współpracy w Office 365. W takim przypadku alerty są wyzwalane i rozpoczyna się proces ograniczania zagrożeń.

Oto na przykład alert, który został wyzwolony z powodu podejrzanego wysyłania wiadomości e-mail:

![Alert został wyzwolony z powodu podejrzanego wysyłania wiadomości e-mail.](/microsoft-365/media/office365atp-suspiciousemailsendalert.jpg)

Oto przykład alertu, który został wyzwolony po osiągnięciu limitu wysyłania dla użytkownika:

![Alert wyzwolony przez wysłanie osiągniętego limitu.](/microsoft-365/media/office365atp-sendinglimitreached.jpg)

## <a name="investigate-and-respond-to-a-compromised-user"></a>Badanie użytkownika z naruszeniem zabezpieczeń i reagowanie na nie

Gdy konto użytkownika zostanie naruszone, alerty są wyzwalane. W niektórych przypadkach to konto użytkownika jest blokowane i nie może wysyłać dalszych wiadomości e-mail, dopóki problem nie zostanie rozwiązany przez zespół ds. operacji zabezpieczeń w organizacji. W innych przypadkach rozpoczyna się zautomatyzowane badanie, które może skutkować zalecanymi akcjami, które powinien podjąć zespół ds. zabezpieczeń.

- [Wyświetlanie i badanie użytkowników z ograniczeniami](#view-and-investigate-restricted-users)

- [Wyświetlanie szczegółów dotyczących zautomatyzowanych dochodzeń](#view-details-about-automated-investigations)

> [!IMPORTANT]
> Musisz mieć odpowiednie uprawnienia do wykonywania następujących zadań. Zobacz [Wymagane uprawnienia do korzystania z funkcji AIR](office-365-air.md#required-permissions-to-use-air-capabilities).

### <a name="view-and-investigate-restricted-users"></a>Wyświetlanie i badanie użytkowników z ograniczeniami

Istnieje kilka opcji przechodzenia do listy użytkowników z ograniczeniami. Na przykład w portalu Microsoft 365 Defender możesz przejść do pozycji **Poczta e-mail & współpracy** \> **Przejrzyj** \> **ograniczonych użytkowników**. Poniższa procedura opisuje nawigację przy użyciu pulpitu nawigacyjnego **Alerty** , który jest dobrym sposobem wyświetlenia różnych rodzajów alertów, które mogły zostać wyzwolone.

1. Otwórz portal Microsoft 365 Defender pod adresem <https://security.microsoft.com> i przejdź do **obszaru Zdarzenia & alerty alertów**\>. Aby przejść bezpośrednio do strony **Alerty** , użyj polecenia <https://security.microsoft.com/alerts>.

2. Na stronie **Alerty** przefiltruj wyniki według okresu i zasad o nazwie **Użytkownik z ograniczeniami wysyłania wiadomości e-mail**.

   :::image type="content" source="../../media/m365-sc-alerts-page-with-restricted-user.png" alt-text="Strona Alerty w portalu Microsoft 365 Defender filtrowana pod kątem użytkowników z ograniczeniami" lightbox="../../media/m365-sc-alerts-page-with-restricted-user.png":::

3. Jeśli wybierzesz wpis, klikając nazwę, zostanie otwarta strona **z ograniczeniami wysyłania wiadomości e-mail** z dodatkowymi szczegółami do przejrzenia. Obok przycisku **Zarządzaj alertem** możesz kliknąć ikonę ![Więcej opcji.](../../media/m365-cc-sc-more-actions-icon.png) **Więcej opcji** , a następnie wybierz pozycję **Wyświetl ograniczone szczegóły użytkownika** , aby przejść do strony **Użytkownicy z ograniczeniami** , na której można [zwolnić użytkownika z ograniczeniami](removing-user-from-restricted-users-portal-after-spam.md).

  :::image type="content" source="../../media/m365-sc-alerts-user-restricted-from-sending-email-page.png" alt-text="Użytkownik nie może wysyłać wiadomości e-mail" lightbox="../../media/m365-sc-alerts-user-restricted-from-sending-email-page.png":::

### <a name="view-details-about-automated-investigations"></a>Wyświetlanie szczegółów dotyczących zautomatyzowanych dochodzeń

Po rozpoczęciu zautomatyzowanego badania możesz zobaczyć jego szczegóły i wyniki w Centrum zgodności & zabezpieczeń. Przejdź do obszaru **Badania** **zarządzania zagrożeniami**\>, a następnie wybierz badanie, aby wyświetlić jego szczegóły.

Aby dowiedzieć się więcej, zobacz [Wyświetlanie szczegółów badania](air-view-investigation-results.md).

## <a name="keep-the-following-points-in-mind"></a>Należy pamiętać o następujących kwestiach

- **Bądź na bieżąco z alertami**. Jak wiesz, tym dłuższy kompromis jest niewykryty, tym większy jest potencjał powszechnego wpływu i kosztów na organizację, klientów i partnerów. Wczesne wykrywanie i terminowe reagowanie mają kluczowe znaczenie dla ograniczenia zagrożeń, a zwłaszcza w przypadku naruszenia zabezpieczeń konta użytkownika.

- **Automatyzacja pomaga, ale nie zastępuje zespołu ds. operacji zabezpieczeń**. Zautomatyzowane możliwości badania i reagowania mogą wykryć naruszonym użytkownikiem na wczesnym etapie, ale twój zespół ds. operacji zabezpieczeń prawdopodobnie będzie musiał zaangażować się w badanie i korygowanie. Potrzebujesz pomocy w tym zakresie? Zobacz [Przeglądanie i zatwierdzanie akcji](air-review-approve-pending-completed-actions.md).

- **Nie polegaj na podejrzanym alertie logowania jako jedynym wskaźniku**. Jeśli konto użytkownika zostanie naruszone, może lub nie może wyzwolić podejrzanego alertu logowania. Czasami jest to seria działań wykonywanych po naruszeniach zabezpieczeń konta, które wyzwalają alert. Chcesz dowiedzieć się więcej o alertach? Zobacz [Zasady alertów](../../compliance/alert-policies.md).

## <a name="next-steps"></a>Następne kroki

- [Przejrzyj wymagane uprawnienia do korzystania z funkcji AIR](office-365-air.md#required-permissions-to-use-air-capabilities)

- [Znajdowanie i badanie złośliwych wiadomości e-mail w Office 365](investigate-malicious-email-that-was-delivered.md)

- [Dowiedz się więcej o środowisku AIR w Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)

- [Odwiedź stronę Microsoft 365 Plan działania, aby zobaczyć, co będzie wkrótce i co się stanie](https://www.microsoft.com/microsoft-365/roadmap?filters=)
