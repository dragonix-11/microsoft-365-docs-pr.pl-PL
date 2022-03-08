---
title: Przykładowy atak wiadomości e-mail wyłudzającej informacje
description: Przekszukaj przykładowy atak, który ma na celu wyłudzanie informacji.
keywords: zdarzenia, alerty, badanie, korelacja, atak, komputery, urządzenia, użytkownicy, tożsamości, tożsamość, skrzynka pocztowa, poczta e-mail, 365, microsoft, m365
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 112bfd63a5f3667b22378790b62f3e33fba784d6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320301"
---
# <a name="example-of-a-phishing-email-attack"></a>Przykładowy atak wiadomości e-mail wyłudzającej informacje

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Microsoft 365 Defender mogą pomóc w wykryciu złośliwych załączników dostarczonych za pośrednictwem poczty e-mail. Ponieważ Centrum [zabezpieczeń Office 365](https://protection.office.com/) i zgodności jest zintegrowane z programem Microsoft 365 Defender, analitycy zabezpieczeń mogą mieć wgląd w zagrożenia pochodzące z programu Office 365, na przykład za pośrednictwem załączników wiadomości e-mail.

Na przykład analitykowi przypisano wieloetapowe zdarzenie.
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-incident.png" alt-text="Przykład zdarzenia wieloetapowego."::: 

Na karcie **Alerty** o zdarzeniu są wyświetlane alerty z usługi Defender Office 365 usługi Microsoft Defender dla aplikacji w chmurze. Analityk może przejść do szczegółów w programie Defender, aby Office 365 alerty, wybierając alerty wiadomości e-mail. Szczegóły alertu są wyświetlane w okienku bocznym.

:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-alerts.png" alt-text="Przykład alertu e-mail.":::
 
Przewijając w dół, jest wyświetlanych więcej informacji, pokazując złośliwe pliki i użytkowników, na które wpływało to zagrożenie.

:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-impact.png" alt-text="Przykład wpływu alertu e-mail na użytkownika i plik.":::
  
Wybranie **opcji Otwórz stronę alertu** umożliwia wyświetlenie określonego alertu, w którym można szczegółowo wyświetlać różne informacje, wybierając link. Rzeczywistą wiadomość e-mail można wyświetlić, wybierając pozycję Wyświetl wiadomości w **Eksploratorze** w dolnej części panelu.
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-event-explorer.png" alt-text="Przykładowe szczegóły alertu."::: 

To przenosi analityka do strony Zarządzanie zagrożeniami, na której są wyświetlane temat wiadomości e-mail, adresaci, nadawcy i inne informacje. **Zap** w **obszarze Akcje specjalne** informuje analityka, że została zaimplementowana funkcja automatycznego przeczyszczania w godzinach zero. Zap automatycznie wykrywa i usuwa złośliwe i spamowe wiadomości ze skrzynek pocztowych w całej organizacji. Aby uzyskać więcej informacji, [zobacz Automatyczne czyszczenie zerowej godziny (ZAP) w programie Exchange Online](../office-365-security/zero-hour-auto-purge.md).

Inne akcje można podjąć w odniesieniu do określonych wiadomości, wybierając pozycję **Akcje**. 
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-actions.png" alt-text="Przykład innych akcji można podjąć w przypadku wiadomości e-mail."::: 

## <a name="next-step"></a>Następny krok

Zobacz [ścieżkę badania opartą na](first-incident-path-identity.md) tożsamości.

## <a name="see-also"></a>Zobacz też

- [Omówienie zdarzeń](incidents-overview.md)
- [Badanie zdarzeń](investigate-incidents.md)
- [Zarządzanie zdarzeniami](manage-incidents.md)
